# eLabFTW crawler
Crawler is python code which accesses the eLabFTW via the API.
Its possible to perform all functions as in the browser via API.

- introduction to API <https://doc.elabftw.net/api.html>
- description of API endpoints <https://doc.elabftw.net/api/v2/>

## Where is the crawler
[crawler code](../code_documentation/pdoc_datastructure_tools/datastructure_tools/elabapi_crawler.html)
At the moment its planned that the crawler is running at a virtual BW-Cloud instance.

Requirements for the instance:
-?

How to setup:

## HighLevel explanation of how crawler works.
I will try to describe the implemented logic of the crawler. 
### Access to DataJoint
Is done in the same way as for individual user. [See here.](../gui_documentation/AdminCommander.md)
However, as no graphical interface is available the _server_settings.json_ needs to be modified via cmd editor such as nano.
~~~~~
nano server_settings.json

ctrl+o to save
ctrl+x to exit
~~~~~
### Pushing animals from DB to eLabFTW


~~~~
written by: Artur
last modified: 2024-01-25
~~~~