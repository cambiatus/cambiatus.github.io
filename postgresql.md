# PostgreSQL

## Intro

PostgreSQL is a powerful, open source object-relational database system.

For information on how to install and get started with PostgreSQL take a look at their official [documentation](https://www.postgresql.org/docs/13/index.html) page.

## Tips

After you are fully setup and running take a look at this section as it might help you. Here we display tips and processes that will help you develop better with PostgreSQL.

**Database dumping** 

Great for testing during development at your local machine. Here is one way of doing:

**Step 1**

Open your terminal and go to your Cambiatus workspace and create a folder to dump database files (folder name example: cambiatus_dbs)
``` 
mkdir <foldername>
```
*Note: The folder name  above is an example, your path may be different*

Open your **psql terminal** and go to the created folder path, for instance:
``` 
cd workspace/cambiatus/cambiatus_dbs
```
*Note: The command above is an example, your path may be different*

**Step 2**

To dump a database called mydb into a SQL-script file:
```
$ pg_dump mydb > db.sql
```
**Step 3**

After unzipping the dumped database file, run the following commands:
```
dropdb -U postgres cambiatus_dev
createdb -U postgres cambiatus_dev
psql cambiatus_dev < db.sql
```
*Note: The command above must be ran in the same directory as the unzipped database file*

For a more detailed step-by-step about [database dumping command and options in Postgres](https://www.postgresql.org/docs/current/app-pgdump.html). 