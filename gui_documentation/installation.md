# DataStructure Tools installation
This module is specifically designed for optophysiology lab
and contains python tools to aid in working with our datastructure.

Requirement git, python >=3.8 <3.10, recommended conda

- How to install/ configure [git for github](github.md)

- How to install conda/miniconda <https://coderefinery.github.io/installation/conda/#conda>

if you have git installed, to download repository: 
	
	git clone https://github.com/Optophys-Lab/DataStructure_tools.git
	cd DataStructure_tools

Install the module with required packages, ideally from a conda env. 
run inside DataStructure_tools

    conda create -n datastructure_tools python=3.9
    conda activate datastructure_tools
    
    pip install -e .

To start GUIs from command-line:

    #make sure $CWD is DataStructure_tools
    python ./datastructure_tools/AnimalCommander.py
    
To start GUIs from python:

    from datastructure_tools.AnimalCommander import AnimalCommander
    AnimalCommander.start_gui()

Occasionally pull the newest version of the code to stay uptodate:

    git pull

read user guides for GUI-tools [general.md](general.md)
~~~~
written by: Artur
last modified: 2024-01-25
~~~~