# Data Structure
This document is a guideline on how to store your scientific data.

The structure of our data server will contain several levels. 

### Level1
Level 1 (Top Level Project) will be under Archive/projects. Top Level Project (e.g. “optoroborat”) typically associated
to a grant.

### Level2
Level 2 (Experiment) An experiment can contain several sessions (e.g. of same cohort, identical manipulation). 
Misc also on level2.
- misc: not session relevant data/ further data about the project. This includes setups, documents, manuals, code,
3D-printer files, literature. It is also intended to include the final manuscript. The final manuscript folder includes figures with metadata (i.e. used animals/sessions etc., code?) and reviewer comments

### Level3
On Level 3, we will have folders: data, results

- results include the analysis of processed data pooled from multiple sessions or animals. Within results there 
should be folders for subresults (e.g. one folder per figure panel). Each subresult folder should include 
the analysis code [this also means information about which animals/sessions etc. are used].

- data will contain the actual data, split into 4 subfolders: **test, 0_raw, 1_preprocessed and 2_processed**.
  - test will be a playground. It has no specific structure and is intended for equipment testing etc. → data that is 
  recorded but without any intention to keep it long term. Each file in this folder *could* be deleted one month after creation.

  0_raw, 1_preprocessed and 2_processed are all ordered in a per session manner. Those can be created automatically by
the [SessionCommander](../gui_documentation/SessionCommander.md) to reduce work and errors. 
Within each of the folders we will have one folder per sessions that are named in this style: 
**yyyymmdd_animal%04d_strain_hhmm**. It contains the date in a yyyymmdd manner, the animal ID always padded to 4 digits,
the strain (because else the animal ID might be ambivalent) and the hhmm of folder creation.
Within each of these session folders there will be folders for each data subtype that has been recorded 
[as defined in the templates](../gui_documentation/AdminCommander.md#experimental-types). 
Within each data subtype folder, we will copy the corresponding files.

More specifically, we envisioned the following for raw, preprocessed and processed:
- 0_raw:  contains raw or semi-raw data which will be kept. If some immediate preprocessing is done after recording 
(e.g., source sync) and there is no reason to redo it, this semi-raw data is kept as "raw". To prevent data loss, 
this folder will be write-protected. You welcome to add meta.json, which contains information about session metadata, experimenter, recording info, files, 
animal etc.

:::{warning}
The automated write protection of raw data is CURRENTLY NOT IMPLEMENTED!
:::

- 1_preprocessed: intermediate processing steps. For the sake of space reduction, the contents should not be stored long
term. Instead, it is meant for short to medium term storage, if access is required but creating is very time-consuming,
e.g. motion correction for 2P, filtering for ephys etc. The idea is that all the further analysis are done on the actual 
processed data and this folder is only needed until the processed data is final. Important, if the raw data is not 
preprocessed, we will keep the folder structure identical as it is in raw, but leave the corresponding preprocessed folder empty.

- 2_processed: finally processed data (reproducible) [e.g. dF/F traces, spike-times, behavioral times …]. We will again
keep the same per session/per filetype folder structure as in raw and preprocessed. The difference now is that we can 
combine the data from several sessions. This allows the pooling of files from several sessions that belong to the same 
experiment for later analysis.

## Example tree
~~~
archive\projects\2023_BehFlex\    #<PROJECT-NAME> [Top Level Project]
├───HillYmaze_training            #<EXPERIMENT-NAME> [Experiment]
│   ├───data                      #data [Data from experiments.. on per-session basis, contains raw/preprocess/processed]
│       ├───0_raw
│       │   ├───20230630_r0083_wt_1431
│       │   │   ├───behav         #data_subtype1
│       │   │   │   └───20230630_r0083_wt_1431_behav.json
│       │   │   ├───behav_vid     #data_subtype2
│       │   │   │   └───20230630_r0083_wt_1431_behav_cam43.mp4
│       │   │   └───daq           #data_subtype3
│       │   │       └───20230630_r0083_wt_1431.bin
│       ├───1_preprocessed        #preprocessed [intermediate processing steps; should not be stored long term/but potentially medium term, if access is required but creating is very time consuming, e.g. motion correction for 2P, filtering for ephys]
│       │   ├───20230630_r0083_wt_1431
│       │   │   ├───behav         #empty because no preprocessing needed
│       │   │   ├───behav_vid
│       │   │   │   └───20230630_r0083_wt_1431_behav_cam43_downsampled.mp4
│       │   │   └───daq
│       │   │       └───20230630_r0083_wt_1431_barcodes.json
│       ├───2_processed           #processed [finally processed data (but can be re-done); e.g. dF/F traces, spike-times, behavioral times ...]
│       │   ├───20230630_r0083_wt_1431
│       │   │   ├───behav
│       │   │   └───behav_vid
│       │   │       └───recording_0_model_HillYmaze_topview_improved
│   └───results                   #results [analysis of processed data from multiple sessions or animals]
├───misc                          #misc [not session relevant data/ further data about the project: setups, documents, manuals, code, 3D-printer files, literature ....]
│   ├───DLC
│   ├───laser_ctr_paper
│   └───etc.
~~~

~~~~
written by: Florian, Artur
last modified: 2024-02-13
~~~~