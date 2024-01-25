# General notes for eLabFTW
For general How-to and user guides please visit <https://doc.elabftw.net/> and <https://doc.elabftw.net/user-guide.html>

Our eLabFTW instance is served by IMBI and is running securely in Freiburg.
<https://eln.imbi.uni-freiburg.de/>

## Some how-to-guides
[register and login](register_login.md)

[generate apikey](generate_apikey.md)

[administration tools](administration_tools.md)

Some short explanation of concepts:
- Experiment vs. resource <https://doc.elabftw.net/user-guide.html#introduction>

## Sync
To synchronize the data from eLabFTW to the DataJoint DB we employ a crawler, this occasionally checks the new or 
modified entries. [Details](crawler.md).

~~~~
written by: Artur
last modified: 2024-01-25
~~~~