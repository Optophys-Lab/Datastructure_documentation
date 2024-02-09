# How to add a new animalsheet entry

To add a new animalsheetentry to the DB for documentation and automated animalsheet creation.

Requirements:
- you are added as user to DB, [if not](../gui_documentation/AdminCommander.md#adding-users) 
- animal is already in the DB, [if not](animalcreation.md)


Options:
1. Use [WeightCommander](../gui_documentation/WeightCommander.md) and enter an entry
2. Enter using the [Animalsheet-experiment](../eLabFTW_documentation/experiment_animalsheet.md) template in eLabFTW. While one can add a file path to the meta field, its not ensured this path actually exists, or is transfered to DB.
3. Use hardcore python to entry to DB.AnimalSheetEntry TODO reference jupyter tutorials

After entering the data via those option, an automated crawler will create up-to-date animal sheets every evening.

[AnimalSheets and signatures](../eLabFTW_documentation/resource_animal.md#animalsheets)

~~~~
written by: Artur
last modified: 2024-02-08
~~~~