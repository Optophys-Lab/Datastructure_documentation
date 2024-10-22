# DataStructure Tools installation
This module is specifically designed for Optophysiology lab
and contains python tools to aid in working with our datastructure.

Requirement git, python >=3.9, recommended conda

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
    python ./datastructure_tools/AdminCommander.py
    
To start GUIs from python:

    from datastructure_tools.AdminCommander import AdminCommander
    AdminCommander.start_gui()

Occasionally pull the newest version of the code to stay uptodate
or use Github Desktop or similar tools to keep the repository up-to-date.

    git pull


::: {dropdown} troubleshooting
If you cannot open any of the commanders due to PyQt6 Errors, try updating PyQt6 via
    
´´´bash
pip uninstall pyqt6
pip install pyqt6
´´´
or install pyqt6-tools
´´´bash
pip install pyqt6-tools
´´´
or install via conda
´´´bash
conda install pyqt
´´´

:::

read user guides for GUI-tools [general.md](general.md)
~~~~
written by: Artur
last modified: 2024-10-22
~~~~