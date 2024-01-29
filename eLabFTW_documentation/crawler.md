## eLabFTW crawler
Crawler is python code which accesses the eLabFTW via the API.
Its possible to perform all functions as in the browser via API.

- introduction to API <https://doc.elabftw.net/api.html>
- description of API endpoints <https://doc.elabftw.net/api/v2/>

## Where is the crawler
[crawler code](../code_documentation/pdoc_datastructure_tools/datastructure_tools/elabapi_crawler.html)
At the moment its planned that the crawler is running at a virtual BW-Cloud instance.
to access the instance using shh

    ssh -i test_schluesser.pem ubuntu@192.xx.42.xxx

test_schluesser.pem and ip are to be acquired from save sources..

### Requirements for the instance:
- ubuntu 22.04 
- inside university firewall
- https and mysql ports open


### How to setup:
- install miniconda
~~~~
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
 ~/miniconda3/bin/conda init bash
~~~~
- create conda env 
~~~~
conda create -n crawler python=3.9
~~~~
- [proceed with datastructure_tools installation](../gui_documentation/installation.md)



## HighLevel explanation of how crawler works
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
Here we push the animal entries which are in the DB to eLabFTW:
TODO add code reference


### Pushing viruses from DB to eLabFTW

~~~~
written by: Artur
last modified: 2024-01-25
~~~~