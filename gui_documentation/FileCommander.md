# FileCommander
This tool can be used to copy the data into correct file structure according to the datastructure rules.

- [Details about datastructure](../datastructure_documentation/datastructure.md)
- [how to create BuildingBlocks and ExpTemplates](AdminCommander.md#building-blocks-of-datastructure)

![filecommander.png](../images/filecommander.png)

1. Select user. Is preselected according to the [saved settings](AdminCommander.md#user-specific-config)
2. List of session from this user, sorted most recent -first
3. Press to open the raw folder of this session on the server (Folder were already created at session creation)
4. Press browse to select files for this types of data modality. The default path which opens for each modality can 
be set in [AdminCommander](AdminCommander.md#user-specific-config). You can also drag and drop files to window in 5
5. List of files to be added for this modality and this session
6. List of files for all session in current Queu
7. Press add to add currently selected files (from 5) to the to copy Q
8. To remove all files from Queu and current selection for this session
9. For all session
10. This executes the file copying. May take a while, the program may appear to hang. Dont close.
11. Check whether the program should verify file integrity after copy. More secure but takes longer.

*. Indicates different building block of the exp template of this experiment there may be more or less of those.

~~~~
written by: Artur
last modified: 2024-01-30
~~~~