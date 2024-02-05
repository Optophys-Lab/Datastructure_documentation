# How to record an animal experiment 

Requirements:
- animal is already in DB


## Case 0: You stay stubborn and do things your way.
Be my guest. But, be aware this is very likely to bite you in the *** at some point later. 

## Case 1: You dont want to read [datastructure](../datastructure_documentation/datastructure.md), but just want to add an entry to the animal sheet.
Meta data about where your data is stored is then not recorded to DB.

Options:
1. Use [WeightCommander](../gui_documentation/WeightCommander.md) and enter a behavior entry
2. Enter using the [Behavior-experiment](../eLabFTW_documentation/experiment_behavior.md) template in eLabFTW. While one can add a file path to the meta field, its not ensured this path actually exists, or is transfered to DB.
3. Use hardcore python to entry to DB.AnimalSheetEntry TODO reference jupyter tutorials

## Case 2: you read the datastructure tutorial and recognized you will thank yourself later for using it
Good on you.

### Use SessionCommander to create and organize your sessions
[SessionCommander](../gui_documentation/SessionCommander.md) will give your session an easily identifiable session_id.
As discussed [previously](../datastructure_documentation/datastructure.md) its has the format **%Y%m%d_animalid_%H%M%S**. SessionCommander will also create the correct 
folder-tree inside your project folder. This will help you organize and find your files.
Session commander also pushes the weight and information about the training to the labbook. Furthermore, metadata of your session will be recorded
to the DataJoint DB, making it easy searchable and integratable into processing pipelines.

### Use FileCommander to organize and copy your files to the correct place on the data server.
[FileCommander](../gui_documentation/FileCommander.md)
You record different data modalities on different computers ? No problem, FileCommander can be used in a distributed manner.
Install [datastructure_tools](../gui_documentation/installation.md) on each computer and just select the correct session and copy the individual files for each modality.
FileCommander 

## Case 3: you would like to automate the folder creation, file copy and documentation
We have build the tools wt reuse in mind. The core functionality of SessionCommander etc. is available as separate modules.
Those can be integrated in your custom software, etc. This will allow you to automate the procession of the session
information, ensure adherence to the structure, reduce your manual work and human error.
The Session class can be import from DB.utils and used to create sessions in DB, folders on the server etc.
Please ask Florian or Artur for details and help in implementing this in your routine.



## How-to delete/modify Sessions
This usually should not be necessarily and is straight a bad practice. Also poorly executed experiments should be 
documented as such. Rather add some notes to the eLabFTW entry or DB. When using SessionCommander there will be
no need to rename folder names or location.

We will occasionally run checks on the entries in DB and compare those with the dataserver. If folders remain empty for 
some time the session will be deleted. (Timelines and execution not decided yet).

You can remove the undesired session from the DB. This will only delete the metadata from DB. The entries to eLabFTW,
if any as well as the files on the dataserver will remain untouched. 

```python
(DB.Session & {'session_id':'session to be deleted'}).delete()
```
## I created a session for the wrong animal
No worries, the session_id can be modified, as well as the corresponding filestructure on the data
server.


~~~~
written by: Artur
last modified: 2024-02-05
~~~~