# PostgreSQL

## Intro

PostgreSQL is a powerful, open source object-relational database system.

For information on how to install and get started with PostgreSQL take a look at their official [documentation](https://www.postgresql.org/docs/13/index.html) page.

## Tips

After you are fully setup and running take a look at this section as it might help you. Here we display tips and processes that will help you develop better with PostgreSQL.

**Database dumping** 

Great for testing during development at your local machine. Here is one way of doing:

**Step 1**

You can connect by SSH to the remote server, do the `pg_dump` call and send the output back to `stdout` of a local machine. Here's an example, replace the names in `UPPER_CASE` with the real ones:

``` 
ssh SSH_USER@SSH_SERVER "pg_dump --exclude-table-data=_block_number_txid -d REMOTE_DB_NAME -h localhost -U REMOTE_DB_USER" > DUMP_NAME.sql 
```
We are excluding the `_block_number_txid` table because it's big and we usually don't need it on the local dev machine.

It will ask for the password for `REMOTE_DB_USER`.

**Step 2**

Undump `DUMP_NAME.sql` to your local DB:

```
psql LOCAL_DB_NAME < DUMP_NAME.sql
```

For a more detailed step-by-step about [database dumping command and options in Postgres](https://www.postgresql.org/docs/current/app-pgdump.html). 