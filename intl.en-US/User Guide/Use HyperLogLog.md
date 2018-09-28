# Use HyperLogLog {#concept_khg_q1z_52b .concept}

HybridDB for PostgreSQL is nested with native features of Greenplum Database, and also supports HyperLogLog. It provides solutions for industries with the Internet advertisement analysis requirements and requirements similar to estimation analysis computing to facilitate quick estimation of PV, UV, and other business metrics.

## Create a HyperLogLog extension { .section}

Run the following command to create a HyperLogLog extension:

```
CREATE EXTENSION hll;
```

## Basic types { .section}

-   Run the following command to create a table containing the hll field:

    ```
    create table agg (id int primary key,userids hll);
    ```

-   Run the following command to convert int to hll\_hashval:

    ```
    select 1::hll_hashval;
    ```


## Basic operators { .section}

-   The hll type supports =, !=, <\>, ||, and \#.

    ```
    select hll_add_agg(1::hll_hashval) = hll_add_agg(2::hll_hashval);
    select hll_add_agg(1::hll_hashval) || hll_add_agg(2::hll_hashval);
    select #hll_add_agg(1::hll_hashval);
    ```

-   The hll\_hashval type supports =, !=, and <\>.

    ```
    select 1::hll_hashval = 2::hll_hashval;
    select 1::hll_hashval <> 2::hll_hashval;
    ```


## Basic functions { .section}

-   The supported functions include hll\_hash\_boolean, hll\_hash\_smallint, hll\_hash\_bigint, and other hash functions.

    ```
    select hll_hash_boolean(true);
    select hll_hash_integer(1);
    ```

-   hll\_add\_agg: Used to convert int to the hll format.

    ```
    select hll_add_agg(1::hll_hashval);
    ```

-   hll\_union: The union of hll.

    ```
    select hll_union(hll_add_agg(1::hll_hashval),hll_add_agg(2::hll_hashval));
    ```

-   hll\_set\_defaults: Used to set the precision.

    ```
    select hll_set_defaults(15,5,-1,1);
    ```

-   hll\_print: Used for debug information.

    ```
    select hll_print(hll_add_agg(1::hll_hashval));
    ```


## Examples { .section}

```
create table access_date (acc_date date unique, userids hll);
insert into access_date select current_date, hll_add_agg(hll_hash_integer(user_id)) from generate_series(1,10000) t(user_id);
insert into access_date select current_date-1, hll_add_agg(hll_hash_integer(user_id)) from generate_series(5000,20000) t(user_id);
insert into access_date select current_date-2, hll_add_agg(hll_hash_integer(user_id)) from generate_series(9000,40000) t(user_id);
postgres=# select #userids from access_date where acc_date=current_date;
     ?column?
------------------
 9725.85273370708
(1 row)
postgres=# select #userids from access_date where acc_date=current_date-1;
     ?column?
------------------
 14968.6596883279
(1 row)
postgres=# select #userids from access_date where acc_date=current_date-2;
     ?column?
------------------
 29361.5209149911
(1 row)
```

