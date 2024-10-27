# DataStructure Tools installation
This module is specifically designed for Optophysiology lab
and contains python tools to aid in working with our datastructure.

Requirement git, python >=3.9, recommended conda

- How to install/ configure [git for github](github.md)

- How to install conda/miniconda <https://coderefinery.github.io/installation/conda/#conda>

## Step1 - Clone repository 
By this we mean create a local copy of the repository on your machine.
If you have git installed, you can do this by running the following command in your terminal:

```bash
git clone https://github.com/Optophys-Lab/DataStructure_tools.git
cd DataStructure_tools
```
this will download the repository to your current working directory.

You can also use Github Desktop/GitKraken or similar tools to clone the repository.

Other option is to download the repository as a zip file from the github page and extract it to your desired location.
This is not recomended as you will not be able to pull the newest version of the code.

## Step2 - Install the module
Install the module with the required packages, ideally from a conda env.

run inside DataStructure_tools folder you just cloned
```bash
conda create -n datastructure_tools python=3.10
conda activate datastructure_tools

pip install -e .
```

## Step3 - Start GUIs
To start GUIs from command-line:

**NEW** for this method current directory does not matter
```bash
python -m datastructure_tools admin
```
OR 

make sure current working directory is DataStructure_tools
```bash
python ./datastructure_tools/AdminCommander.py
```   

To start GUIs from python:

```python
from datastructure_tools.AdminCommander import AdminCommander
AdminCommander.start_gui()
```
Other tools start in similar manner, just replace AdminCommander with the desired tool.

## Step4 - configure your installation
Enter the required information in the [AdminCommander](AdminCommander.md) to configure your installation.

Occasionally pull the newest version of the code to stay uptodate
or use Github Desktop or similar tools to keep the repository up-to-date.
```bash
git pull
```

::: {dropdown} Troubleshooting
If you cannot open any of the commanders due to PyQt6 Errors, try updating PyQt6 via
    
```bash
pip uninstall pyqt6
pip install pyqt6
```
or install pyqt6-tools
```bash
pip install pyqt6-tools
```
or install via conda
```bash
conda install pyqt
```
:::

read user guides for GUI-tools [general.md](general.md)
~~~~
written by: Artur
last modified: 2024-10-27
~~~~