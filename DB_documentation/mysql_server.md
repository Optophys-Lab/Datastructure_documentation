# Some MYSQL related commands for reference

connect to the mysql database
~~~~~~~~
mysql --host=10.x.26.xxx --user=optouser -p
~~~~~~~~

backup
~~~~~~~~
mysqldump --host=10.x.26.xxx --user=as153 -p opto_db > path2backup/"$DBbackup_(date '+%Y%m%d').sql"
~~~~~~~~

Some mysql syntax:

> show databases; # show databases
> 
> use opto_db_test; # select a database
> 
> show tables;  # show tables in the database

To drop lookup tables with # in the name use ``
~~~~~~~~
DROP TABLE `#table`;
~~~~~~~~

To delete part-tables or other tables which fail due to Foreigh-key check one can disable it. Please use with caution.
~~~~~~~~
SET FOREIGN_KEY_CHECKS=0; -- to disable them
SET FOREIGN_KEY_CHECKS=1; -- to re-enable them
~~~~~~~~


~~~~
written by: artur 
last modified: 2024-01-24
~~~~