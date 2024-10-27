# DataStructure_tools

python tools to aid in working with our future datastructure

Requirement git, python >=3.9
if you have git installed:

```none
git clone https://github.com/Optophys-Lab/DataStructure_tools.git
cd DataStructure_tools
```

Install the module with required packages, ideally from a conda env.
run inside DataStructure_tools

```none
conda create -n datastructure_tools python=3.9
conda activate datastructure_tools

pip install -e .
```

To start GUIs from command-line:
#make sure current directory is DataStructure_tools

```none
python ./datastructure_tools/AdminCommander.py
```

or *NEW*: for this method current directory doesnt matter

```none
python -m datastructure_tools admin
```

To start GUIs from python:

```none
from datastructure_tools.AnimalCommander import AnimalCommander
AnimalCommander.start_gui()
```

## Tutorial

To get you started, we provide a tutorial notebook in Tutorial.ipynb.
It is a work in progress and will be updated continously. So make sure to pull the git once in a while!

## Modules:

*AdminCommander* - GUI for managing server connection as well as user settings.
Projects, Experiments and datatypes can be created here, as well as atlas files copy

*AnimalCommander* - GUI to create and add Animals to the DB
can be used standalone or be called from SessionCommander

*FileCommander* - GUI to copy files into corresponding folders
can be used standalone or be called from SessionCommander

*SessionCommander* - GUI to create and Sessions to DB
and create the corresponding folder structure on the server

*DataBaseAccess* -  a class abstracting the schema activation and DJ access
is used in GUIs and can be used standalone

*SurgeryCommander* - GUI to add information about surgeries, includes insertion
angles calculation and atlas projections

*SurgeryPlanner* - GUI for planning of surgeries at different angles

*WeightCommander* - GUI to add weights of animals to DB and create animal sheets
in automated manner

*VirusCommander* - GUI to add Virus related infos to the DB

*EquipmentCommander* - GUI to add EphysProbes and its types to the DB,
with visualisation of said probes

*LabbookCommander* - GUI for creation of animal training sheets from the DB

## Known issues

If you run

```none
import_datastructure_tools as dt
dt.AdminCommander.start_gui()
```

and get a module not found error, this might be due to a bug with pyqt. Try opening the commanders by going to the folder and running

```none
python AdminCommander.py
```

If you cannot open any of the commanders due to PyQt6 Errors, try updateting PyQt6 via

```none
pip uninstall pyqt6
pip install pyqt6
```
