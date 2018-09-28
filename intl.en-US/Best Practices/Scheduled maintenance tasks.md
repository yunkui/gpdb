# Scheduled maintenance tasks {#concept_nzk_xtf_v2b .concept}

When an update operation \(including INSERT VALUES, UPDATE, DELETE, and ALTER TABLE ADD COLUMN\) is performed on a system, junk data that may no longer be used is left in the system table and the updated data table. This junk data reduces the system performance and takes up a large amount of disk space. We recommend that you clear such data on a regular basis by following the methods provided in this document.

## Clear junk data without locking the table { .section}

You can clear some junk data without locking the table. The method is as follows.

-   Command: connect to every database, log on to the database as the database owner, and run the `VACUUM` command.

-   Frequency: at least once a day.

    -   If data is updated in real time \(that is, INSERT VALUES, UPDATE, and DELETE operations are performed continuously\), we recommend that you run the `VACUUM` command once every two hours.
    -   If data update is performed by bulk once a day, you can run the command once after the bulk update every day.
-   Impact to the system: no table is locked, and tables can be read and written to normally. But it may increase the CPU and I/O usage, and impact query performance.

-   Example: you can use the following Linux Shell script file and run it as a scheduled crontab task.


```
#!/bin/bash
export PGHOST=myinst.gpdb.rds.tbsite.net
export PGPORT=3432
export PGUSER=myuser
export PGPASSWORD=mypass
#do not echo command, just get a list of db
dblist=`psql -d postgres -c "copy (select datname from pg_stat_database) to stdout"`
for db in $dblist ; do
    #skip the system databases
    if [[ $db == template0 ]] ||  [[ $db == template1 ]] || [[ $db == postgres ]] || [[ $db == gpdb ]] ; then
        continue
    fi
    echo processing $db
    #vacuum all tables (catalog tables/user tables)
    psql -d $db -e -a -c "VACUUM;"
done
```

## Clear junk data during maintenance windows { .section}

You can clear all junk data during maintenance windows of services when services are suspended. The method is as follows.

-   Command: connect to every database, and log on to the database as the database owner \(you must have the owner permission for all the operation objects\).

    1.  Run the `REINDEX SYSTEM <database name>` command.
    2.  Run the `VACUUM FULL <table name>`, `REINDEX TABLE <table name>` command on every data table \(non-system table\).
-   Frequency: at least once per week. If almost all the data is updated every day, you can run the command once a day.

-   Impact on the system: the command locks tables for VACUUM FULL or REINDEX and these tables become not readable or writable. This may increase the CPU and I/O usage.

-   Example: you can use the following Linux Shell script file and run it as a scheduled crontab task.


```
#!/bin/bash
export PGHOST=myinst.gpdb.rds.tbsite.net
export PGPORT=3432
export PGUSER=myuser
export PGPASSWORD=mypass
#do not echo command, just get a list of db
dblist=`psql -d postgres -c "copy (select datname from pg_stat_database) to stdout"`
for db in $dblist ; do
    #skip system databases
    if [[ $db == template0 ]] ||  [[ $db == template1 ]] || [[ $db == postgres ]] || [[ $db == gpdb ]] ; then
        continue
    fi
    echo processing db "$db"
    #do a normal vacuum
    psql -d $db -e -a -c "VACUUM;"
    #reindex system tables firstly
    psql -d $db -e -a -c "REINDEX SYSTEM $db;"
    #use a temp file to store the table list, which could be vary large
    cp /dev/null tables.txt
    #query out only the normal user tables, excluding partitions of parent tables
    psql -d $db -c "copy (select '\"'||tables.schemaname||'\".' || '\"'||tables.tablename||'\"' from (select nspname as schemaname, relname as tablename from pg_catalog.pg_class, pg_catalog.pg_namespace, pg_catalog.pg_roles where pg_class.relnamespace = pg_namespace.oid and pg_namespace.nspowner = pg_roles.oid and pg_class.relkind='r' and (pg_namespace.nspname = 'public' or pg_roles.rolsuper = 'false' ) ) as tables(schemaname, tablename) left join pg_catalog.pg_partitions on pg_partitions.partitionschemaname=tables.schemaname and pg_partitions.partitiontablename=tables.tablename where pg_partitions.partitiontablename is null) to stdout;" > tables.txt
    while read line; do
        #some table name may contain the $ sign, so escape it
        line=`echo $line |sed 's/\\\$/\\\\\\\$/g'`
        echo processing table "$line"
        #vacuum full this table, which will lock the table
        psql -d $db -e -a -c "VACUUM FULL $line;"
        #reindex the table to reclaim index space
        psql -d $db -e -a -c "REINDEX TABLE $line;"
    done <tables.txt
done
```

