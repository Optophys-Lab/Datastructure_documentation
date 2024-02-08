# DB backend information
DataJoint is a wrapper for mySQL databases. Our database is a MariaDB running at IMBIT.
The data is backup daily. For administrative details contact IT-administrator.

To access data directly without DataJoint you will require mysql.

```bash
sudo apt install mysql
```

## Some MYSQL related commands for reference
connect to the mysql database:
```bash
mysql --host=10.x.26.xxx --user=optouser -p
```

backup
```bash
mysqldump --host=10.x.26.xxx --user=as153 -p opto_db > path2backup/"$DBbackup_(date '+%Y%m%d').sql"
```

Some mysql syntax:

```mysql
show databases; # show databases
use opto_db_test; # select a database
show tables;  # show tables in the database
```

To drop lookup tables with # in the name use ``
```mysql
DROP TABLE `#table`;
```

To delete part-tables or other tables which fail due to Foreigh-key check one can disable it. Please use with caution.
```mysql
SET FOREIGN_KEY_CHECKS=0; -- to disable them
SET FOREIGN_KEY_CHECKS=1; -- to re-enable them
```


~~~~
written by: Artur 
last modified: 2024-02-06
~~~~