# API reference

## Classes for general functionality

### datastructure_tools.utils.CreateDataStructureNew(path2proj, pipeline, Project, Experiment, sessionName, debug=True, overrule=False)

debug - only print structure dont create
pipeline has to contain a dict with keys like 0_raw with a list of folders to create

### *class* datastructure_tools.utils.SessionClass(DB, test=False, \*args, \*\*kwargs)

class abstracting all infos about the session
can be reused in functions

Required inputs:
DB -  handle to DataBaseAccess
animal_id -> str animal id in DB, will be checked
session_datetime
session_note -> str can be not provided
project -> str project in DB, will be checked
user -> str user in DB, will be checked
expName -> str experiment name folder
experiment_template -> str experiment_type name will be checked

probably new way to use it:

  session = SessionClass(self.DB, animal_id=AnimalName2use, session_datetime=session_datetime,
                            session_note=’This is a tutorial note’, project=’2020_testproject’,
                            user=’tt1010’, expName=’totally_real_experiment’,
                            experiment_template = ‘tutorial_experiment’, weight = ‘9999’, test = True)
  session.pushWholeSessionInfo2DB()

old way to use it how to use:
# session = SessionClass(self.DB, animal_id=AnimalName2use, session_datetime=session_datetime,
#                            session_note=self.Session_note.toPlainText(), project=self.Project_combo.currentText(),
#                            user=self.User_combo.currentText(), expName=self.ExpName_combo.currentText(),
#                            experiment_template = self.ExpType_combo.currentText(),test = BOOL if a test session)

#pathcreationSuccess = session.createSession_path() # create Paths on server
# TRUE if worked
#PushSuccess = session.checkInputs() # checks inputs and pushes to DB
# TRUE if worked
#session.weight = float(self.AnimalWeightEdit.text())
#session.weight_note = self.WeightNoteEdit.text()
#session.pushWeights()

#### pushWholeSessionInfo2DB(\*\*kwargs)

puts the session to DB with weights, Adds to Animalsheet entry and eLabFTW(both session entry and Animalsheet)
use instead of checkInputs adn pushWeights
all AnimalSheets fields to be entered should be pass as kwargs to the function eg.g
pushSession2DB(housing=”Gruppe”,weiterleben=True .. etc.)

### datastructure_tools.utils.add_row_to_animalsheet_df(current_animal_sheet, data_to_add, abbruchgewicht=None)

takes a dataframe of an animal sheet and adds a row to that
if abbruchgewicht is none: abbruchgewicht will be 0.8\*weight

### datastructure_tools.utils.change_animal_nr(DB, session_id: str, new_animal: str)

function for renaming a Session if the animal id was wrongly entered, copies and renames the files as well
:param DB: DataBaseAccess instance
:param session_id: (str) session_id to be changed
:param new_animal: (str) correct animal id

Returns:

### datastructure_tools.utils.convert_date_from_animalsheet_back_to_pydate(animal_sheet_date, date_format='%d/%m/%Y')

usage: pydate_obj = convert_date_back_to_pydate(animal_sheet.iloc[0][‘Datum und Wochentag’])

### datastructure_tools.utils.create_probe_from_probeinterfacefile(path2file: str) -> (<class 'list'>, <class 'probeinterface.probe.Probe'>)

This creates and add the corresponding probe from a probeinterface_file
:param path2file: path 2 json file to be read in spike interface

* **Returns:**
  list of dictionaries with electrode properties
  Probe file for plotting

### datastructure_tools.utils.dict_to_uuid(key: dict)

Given a dictionary key, returns a hash string as UUID
:param key: Any python dictionary
:type key: dict

### datastructure_tools.utils.dict_to_uuid_my(key: dict)

Given a dictionary key, returns a hash string as UUID this is better as it sorts nested dict

* **Parameters:**
  **key** (*dict*) – Any python dictionary

### datastructure_tools.utils.find_server_directory(root_directories: list) → Path

Given multiple potential server directories, return correct root.
Search and return one directory that is the parent of the given path.
:param root_directories: potential root directories
:type root_directories: list

* **Returns:**
  root_directory (pathlib.Path object)
* **Raises:**
  **FileNotFoundError** – No valid root directory

### datastructure_tools.utils.get_Abbruchgewicht(DB, animal_id: str, weight_date: datetime) → float

given animal_id and a datetime returns abbruchgewicht for this AnimalSheetEntry
:param DB: DataBaseAccess instance
:param animal_id: str
:param weight_date: datetime of the entry in AnimalSheetEntry

* **Returns:**
  Abbruchgewicht in g
* **Return type:**
  float

### datastructure_tools.utils.get_AbbruchgewichtList(DB, animal_id: str) → list

given animal_id return a list of abbruchgewichte for each AnimalSheetEntry
:param DB: DataBaseAccess instance
:param animal_id: str

* **Returns:**
  list

### datastructure_tools.utils.json_serial(obj)

JSON serializer for objects not serializable by default json code

### datastructure_tools.utils.make_animalsheet_byanimal_id(DB, animal_id: str, savepath: [<class 'str'>, <class 'pathlib.Path'>] = None) → [<class 'pathlib.Path'>, None]

wrapper for the make_animalsheet_whole, without user mapping and signatures
:param DB: DataBaseAccess instance
:param animal_id: str animal_id
:param savepath: optional path 2 save

* **Returns:**
  path of the created animal_sheet

### datastructure_tools.utils.remove_wd_fromentries(DB, animal_id: str)

removes the WD from the procedure field of the animalsheet entry
:param DB: DataBaseAccess instance
:param animal_id: str of the animal id
:return:

### datastructure_tools.utils.sort_animalsheet_df_by_date(animal_sheet_to_sort)

I guess there is an easier way to do this but here we are
usage: sorted_animal_sheet = sort_animalsheet_by_date(animal_sheet)

<a id="module-datastructure_tools.Surgery_classes"></a>

classes to work with Surgery data, injections, implantation, etc.
Autor: Artur

### *class* datastructure_tools.Surgery_classes.ProbeImplant(\*\*kwargs)

this is not finished

#### show_on_atlas(ax=None)

does Probe specific modifications plots the probeinterface plot

### *class* datastructure_tools.Surgery_classes.Window(DB, \*\*kwargs)

this is not finished

## GUIs

## eLabFTW crawler

### *class* datastructure_tools.eLabFTW_api_utils.AnimalFields

enum for fields in Animal in ELN

### *class* datastructure_tools.eLabFTW_api_utils.FieldTypes

this class enums the names for the different FieldTypes in eLabFTW

### *class* datastructure_tools.eLabFTW_api_utils.PerfusionFields

enum Class for the Perfusion Template in ELN

### *class* datastructure_tools.eLabFTW_api_utils.VirusFields

enum for fields for virus in ELN

### *class* datastructure_tools.eLabFTW_api_utils.expStatus

this class enums the names for the different experiment status in eLabFTW

### datastructure_tools.eLabFTW_api_utils.get_fields_fromclass(cls) → list

takes a class and returns list of the attributes of this class
:param cls: the class to be checked

Returns: list of attributes

### *class* datastructure_tools.eLabFTW_api_utils.itemStatus

this class enums the names for the different itemStatus in eLabFTW
