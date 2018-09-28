# Basic operations {#concept_jk2_try_52b .concept}

HybridDB for PostgreSQL is consistent with Greenplum Database in operations based on Greenplum Database, including the schema, supported types, and user permissions. Aside from some operations exclusive to Greenplum Database, such as the Distribution Key and AO table, you can refer to PostgreSQL for all the other operations.

This document introduces the basic operations of HybridDB for PostgreSQL, including [creating a database](#), [creating a distribution key](#), [constructing data](#), and [creating a query](#).

## Create a database {#database .section}

In HybridDB for PostgreSQL instances, you can use SQL statements to create a database following the same operations in PostgreSQL. For example, after an instance is connected to Greenplum through the psql tool, run the following command to create a database:

```
=> create database mygpdb;
CREATE DATABASE
=> \c mygpdb
psql (9.4.4, server 8.3devel)
You are now connected to database "mygpdb" as user "mygpdb".
```

## Create a distribution key {#distributionkey .section}

In HybridDB for PostgreSQL, tables are distributed on all of the Segments following a hash or random distribution rule. You can specify the distribution key when creating a table. By doing this, data imported is assigned to the specific Segment according to the hash value calculated by the distribution key.

```
=> create table vtbl(id serial, key integer, value text, shape cuboid, location geometry, comment text) distributed by (key);
CREATE TABLE
```

When no distribution key is specified, that is, with no “distributed by \(key\)” followed in the command, Greenplum randomizes the ID field using the round-robin approach.

## Best practices { .section}

Distribution keys are vital to query performance. When you are specifying distribution keys, we recommend that you follow the “Even” principle. What’s more, specifying a more business-cued field can significantly improve the performance.

To be specific, the best practices include:

-   Select the evenly distributed columns or multiple columns to prevent data from tilting.

-   Select the fields commonly used in JOIN, especially for statements with high concurrency.

-   Select the condition columns with high concurrent query and high filter rate.

-   Do not use random distribution.


For details, see [Reference](#reference).

## Construct data {#constructdata .section}

1.  Create a function to generate a random string.

    ```
    CREATE OR REPLACE FUNCTION random_string(integer) RETURNS text AS $body$
    SELECT array_to_string(array
                          (SELECT substring('0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'
                                            FROM (ceil(random()*62))::int
                                            FOR 1)
                           FROM generate_series(1, $1)), ''); 
    $body$ 
    LANGUAGE SQL VOLATILE;
    ```

2.  Create a distribution key.

    ```
    CREATE TABLE tbl(id serial, KEY integer, locate geometry, COMMENT text) distributed by (key);
    ```

3.  Construct data.

    ```
    INSERT INTO tbl(KEY, COMMENT, locate) 
     SELECT 
         KEY, 
         COMMENT, 
         ST_GeomFromText(locate) AS locate 
     FROM
         (SELECT 
             (a + 1) AS KEY, 
             random_string(ceil(random() * 24)::integer) AS COMMENT, 
             'POINT(' || ceil(random() * 36 + 99) || ' ' || ceil(random() * 24 + 50) || ')' AS locate 
         FROM 
             generate_series(0, 99999) AS a) 
         AS t;
    ```


## Create a query {#createaquery .section}

-   Query

    ```
      => select * from tbl where key = 751;
      | id  | key | value | shape        | locate                                     | comment        |
      +-----+-----+-------+--------------+--------------------------------------------+----------------+
      | 751 | 751 | red   | 01010000000000000000C05B400000000000004A40 | B9hPhjeNWPqV |
      (1 row)
      Time: 513.101 ms
    ```

-   Query plan

    ```
      => explain select * from tbl where key = 751;
      Gather Motion 1:1  (slice1; segments: 1)  (cost=0.00..1519.28 rows=1 width=53)
        ->  Seq Scan on tbl  (cost=0.00..1519.28 rows=1 width=53)
              Filter: key = 751
      Settings:  effective_cache_size=8GB; gp_statistics_use_fkeys=on
      Optimizer status: legacy query optimizer
    ```


## Reference {#reference .section}

-   [Pivotal Greenplum Official Documentation](http://gpdb.docs.pivotal.io/4380/common/welcome.html)

-   [Greenplum 4.3 Best Practices](http://gpdb.docs.pivotal.io/4300/pdf/GPDB43BestPractices.pdf)


