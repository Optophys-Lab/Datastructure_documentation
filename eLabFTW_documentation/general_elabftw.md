# General notes for eLabFTW
For general How-to and user guides please visit <https://doc.elabftw.net/> and <https://doc.elabftw.net/user-guide.html>

Our eLabFTW instance is served by IMBI and is running securely in Freiburg.
<https://eln.imbi.uni-freiburg.de/>

## Some general how-to-guides
- [register and login](register_login.md)
- [generate apikey](generate_apikey.md)
- [administration tools](administration_tools.md)

## Guides for individual templates
- [Behavior Exp Entry](experiment_behavior.md)
- [Perfusion Entry](experiment_perfusion.md)
- [Surgery Entry](experiment_surgery.md)
- [Waterdeprivation Entry](experiment_waterdep.md)
- [AnimalSheetEntry](experiment_animalsheet.md)
- [Animal Template](resource_animal.md)
- [Virus Template](resource_virus.md)



## Sync
To synchronize the data from eLabFTW to the DataJoint DB we employ a crawler, this occasionally checks the new or 
modified entries. [Details](crawler.md).

Some entries entered via [datastructure_tools](../gui_documentation/general.md) are automatically pushed to eLabFTW via 
*eLabbookCommander* TODO add reference to code 

~~~~
written by: Artur
last modified: 2024-02-05
~~~~