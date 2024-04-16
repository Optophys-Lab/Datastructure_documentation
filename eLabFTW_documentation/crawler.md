## eLabFTW crawler
Crawler is python code which accesses the eLabFTW via the API.
Its possible to perform all functions as in the browser via API.

- introduction to API <https://doc.elabftw.net/api.html>
- description of API endpoints <https://doc.elabftw.net/api/v2/>

## Where is the crawler
[crawler code](../code_documentation/pdoc_datastructure_tools/datastructure_tools/elabapi_crawler.html)
At the moment its planned that the crawler is running at a virtual BW-Cloud instance.
to access the instance using shh

    ssh -i test_schluesser.pem ubuntu@192.xx.42.xxx

test_schluesser.pem and ip are to be acquired from save sources..

### Requirements for the instance:
- ubuntu 22.04 
- inside university firewall
- https and mysql ports open


### How to setup:
- install miniconda
~~~~
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
 ~/miniconda3/bin/conda init bash
~~~~
- create conda env 
~~~~
conda create -n crawler python=3.9
~~~~
- [proceed with datastructure_tools installation](../gui_documentation/installation.md)

install de_DE.UTF8 locale as BW-Cloud does not have it by default
~~~~
sudo apt-get install language-pack-de
sudo dpkg-reconfigure locales
~~~~


## HighLevel explanation of how crawler works
I will try to describe the implemented logic of the crawler. 
### Access to DataJoint
Is done in the same way as for individual user. [See here.](../gui_documentation/AdminCommander.md)
However, as no graphical interface is available the _server_settings.json_ and _user_settings.json_ need
to be modified via cmd editor such as nano.
~~~~~
nano ./datastructure_tools/DataJoint/server_settings.json
nano ./datastructure_tools/user_settings.json

ctrl+o to save
ctrl+x to exit
~~~~~
[Datastructure tools](..%2Fgui_documentation%2Finstallation.md) are installed and a conda environment.
TODO, maybe move to docker container ?


## Scheduled task
The crawler is running a scheduler to run different jobs at different timepoints.
- every minute - new entries from surgeries, animalsheets, perfusions
- every 2 minutes, animals, viruses and updates to all templates with newest state of animals.
- every 5 minutes the crawler signs a "healthentry" of Maintance category resource, this is used to visualize the status
- every day the crawler creates AnimalSheets and uploads those to the corresponding animal

### Crawling for animals
- read current animals in DB
- read entries in eLabFTW (of resource category animals)
- load the meta fields
- check:
  - delivery date is entered 
  - animal_nr is entered and is int
  - age at delivery is a float
  - user entered or if not take the creator as user
    - checks that user as orgid (RZ-kuerzel)
  - animal note is take from main text body
- if no errors so far, tries to push to DB, *DB.Animal*
- if errors, comments on the entry
- if push successful, changes title to animal_id
- adds tva as a tag to the entry
- comments success
- logs entry

### Crawling for viruses
- reads viruses in DB
- read entries in eLabFTW (of resource category virus)
- load the meta fields
- check:
  - delivery date is entered   
- if no errors so far, tries to push to DB *DB.Virus*
- if errors, comments on the entry
- if push successful, changes title to virus#batch_nr
- adds tva as a tag to the entry
- comments success
- logs entry

### Crawling for behavioral entries
**crawl4Sessions**
- reads entries in eLabFTW (of resource category Behavior and locked!)
- checks if entry was already crawled (DB entry)
- loads the meta fields
- creates a session_id
- *DB.Session*

### Crawling for perfusions
**crawl4Perfusions**
- reads entries in eLabFTW (of resource category Perfusion and locked!)
- checks if entry was already crawled (DB entry)
- loads the meta fields
- checks for animal_id
- pushes to DB *DB.Animal.Death*
- Creates animalsheet entry with some pre-filled fields:
  - procedure: f"Euthanasia,{perfusion_d['drugs']} Perfusion"
  - weiterleben: 'Toetung'
        

### Crawling for water deprivations
**crawl4Waterdeprivation**
- read entries in eLabFTW (of resource category WaterDeprivation and locked!)
- checks if entry was already crawled (DB entry)
- loads the meta fields
- pushes to DB: *DB.ZWR*
- Creates animalsheet entry with some pre-filled fields:
  -  procedure: f'Kontrolle und Beginn der Wasserdeprivation, ZWR:{ZWR}'

### Crawling for animal sheets
**crawl4AnimalSheetEntries**
- read entries in eLabFTW (of resource category AnimalDocumentation and locked!)
- checks if entry was already crawled (DB entry)
- loads the meta fields
- pushes to DB *DB.AnimalSheetEntry*

### Crawling for surgeries
**crawl4Surgeries**
- read entries in eLabFTW (of resource category Surgery and locked!)
- checks if entry was already crawled (DB entry)
- load the meta fields
- check:
  - surgery date is entered 
  - animal_nr is entered and is int
  - age at delivery is a float
  - user entered 
- checks if entry is already inDB via animal_id and surgery datetime
- pushed to DB *DB.Surgery*
- logs idx as crawled
- puts animal_id as tag
- link animal to entry
- puts tva as tag if avaible
- creates an animalsheet entry in DB and eLabFTW (links to this entry) 
 
## Pushes
At initialization the crawler can push current state of the DB to eLabFTW.
The templates for individual entries are designed in a way that the fields have same names as in 
DB, this allows easy exchange via dictionaries.

### Categories
are created from classes **ResourceCategories** and **ExperimentCategories**,
**get_expCategory_id** returns the category id or creates if not available yet.
Individual categories are subclass of the corresponding class. This is done so to ensure consistent naming and 
to use those names as ENUMS.

### Templates
Templates can be designed in the browser or programatically
Here we use classes like **WaterDeprivationFields**. 
In there subclasses represent individual meta fields to be entered.
properties such as field type are set from **FieldTypes**.
Important here: the class name needs to corrsepond to the field name in DB if it is to be filled or transfered to DB.
the name displayed to user is defined in property *name*.
The order of fields can be defined via property *position* (1 based).
property *required*, tries to indicate to user that a fields is required but does not enforce it.

### Pushing animals from DB to eLabFTW
template **AnimalFields** from eLabFTW_api_utils
**pushAnimalsDB2ELN** - function pushes the animal entries which are in the DB to eLabFTW:
- reads animals from DB
- reads animals from eLabFTW (Resources of category Animals) consideres the title of each entry as animal_id
- checks whether the animal is already in eLabFTW
- fills the template fields from DB

### Pushing viruses from DB to eLabFTW
template **VirusFields** from eLabFTW_api_utils
**pushVirusDB2ELN** - function pushes the viruses entries which are in the DB to eLabFTW:
- reads viruses from DB
- reads viruses from eLabFTW (Resources of category Virus) reads virus and batch via title f"{virus['virus']}#{virus['batch_nr']}"
- checks whether the virus is already in eLabFTW
- fills the template fields from DB


~~~~
written by: Artur
last modified: 2024-02-22
~~~~