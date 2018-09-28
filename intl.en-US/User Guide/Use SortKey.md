# Use SortKey {#concept_nrh_nd2_v2b .concept}

SortKey is a table attribute that helps store data in the order of the SortKey to files on a disk. SortKey offers the following advantages:

-   Speed up column-store optimization. The min and max meta information it collects seldom overlaps with each other, featuring good filtering friendliness.

-   Avoid sorting SQL data containing “order by” and “group by” for a second time. The data directly read from the disk is ordered as required by the sorting conditions.


This document describes the usage of SortKey in different use cases.

## Define the SortKey { .section}

You can use the `CREATE TABLE` command to define a new table containing a SortKey. The syntax is as follows:

```
CREATE [[GLOBAL | LOCAL] {TEMPORARY | TEMP}] TABLE table_name (
[ { column_name data_type [ DEFAULT default_expr ]     [column_constraint [ ... ]
[ ENCODING ( storage_directive [,...] ) ]
]
   | table_constraint
   | LIKE other_table [{INCLUDING | EXCLUDING}
                      {DEFAULTS | CONSTRAINTS}] ...}
   [, ... ] ]
   [column_reference_storage_directive [, ] ]
   )
   [ INHERITS ( parent_table [, ... ] ) ]
   [ WITH ( storage_parameter=value [, ... ] )
   [ ON COMMIT {PRESERVE ROWS | DELETE ROWS | DROP} ]
   [ TABLESPACE tablespace ]
   [ DISTRIBUTED BY (column, [ ... ] ) | DISTRIBUTED RANDOMLY ]
   [ SORTKEY (column, [ ... ] )]
   [ PARTITION BY partition_type (column)
       [ SUBPARTITION BY partition_type (column) ]
          [ SUBPARTITION TEMPLATE ( template_spec ) ]
       [...]
    ( partition_spec )
        | [ SUBPARTITION BY partition_type (column) ]
          [...]
    ( partition_spec
      [ ( subpartition_spec
           [(...)]
         ) ]
    )
```

**Example**

```
create table test(date text, time text, open float, high float, low float, volume int) with(APPENDONLY=true,ORIENTATION=column) sortkey (volume);
```

## Sort the table { .section}

The command is as follows:

```
VACUUM SORT ONLY [tablename]
```

**Change the SortKey**

The command is as follows:

```
ALTER [[GLOBAL | LOCAL] {TEMPORARY | TEMP}] TABLE table_name SET SORTKEY (column, [ ... ] )
```

**Note:** 

This command only changes `catalog` without sorting the data immediately. To sort data, you must use the `VACUUM SORT ONLY` command.

**Example**

```
alter table test set sortkey (high,low);
```

**Note:** 

After you update a table \(such as Insert, Update, and Delete\), data in the table is deemed as non-SortKey-ordered. Data read from the disk for a query is not regarded as ordered. In this case, you must rerun the `VACUUM SORT ONLY` command to re-organize data in the table.

