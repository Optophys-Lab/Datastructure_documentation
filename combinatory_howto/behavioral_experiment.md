# How to record an animal experiment 

Requirements:
- animal is already in DB

Case 1: You dont want to read [datastrucuture](../datastructure_documentation/datastructure.md), but just one to add an entry to animal sheet.
Meta data about where your data is stored is then not recorded to DB
1. Use [WeightCommander](../gui_documentation/WeightCommander.md) and enter a behavior entry
2. Entry using the [Behavior-experiment](../eLabFTW_documentation/experiment_behavior.md). While one can add a file path to the data in a field. its not ensured this path actually exists, or is transfered to DB.
3. Use hardcore python to entry to DB.AnimalSheetEntry TODO reference jupyter tutorials

Case 2: you read the datastructure tutorial and recognized you will thank yourself later for using it.


~~~~
written by: Artur
last modified: 2024-02-01
~~~~