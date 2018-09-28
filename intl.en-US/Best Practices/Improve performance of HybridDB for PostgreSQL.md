# Improve performance of HybridDB for PostgreSQL {#concept_znx_ct2_v2b .concept}

HybridDB for PostgreSQL is developed based on Greenplum Database and is enhanced with some in-depth extensions by Alibaba Cloud. It is a distributed cloud database that is composed of multiple [groups](https://www.alibabacloud.com/help/doc-detail/35402.htm) to provide MPP \(Massively Parallel Processing\) data warehousing service.

This document introduces the best practices for using HybridDB for PostgreSQL. We recommend that you choose from the mentioned methods to follow in order to improve the performance of HybridDB for PostgreSQL, speed up the import process, and reduce the cost.

## Use Compressed Column Storage { .section}

For tables with infrequent updates and many fields, we recommend that you use Compressed Column Storage. This method increases the compression ratio three-fold while guaranteeing performance, and the import speed is usually faster.

For example, you can add the clause `WITH (APPENDONLY=true, ORIENTATION=column, COMPRESSTYPE=zlib, COMPRESSLEVEL=3, BLOCKSIZE=1048576)` to the tabulation statements to create compressed column store tables.

For the specific syntax, see [CREATE TABLE](http://gpdb.docs.pivotal.io/4380/ref_guide/sql_commands/CREATE_TABLE.html).

## Use the Nested Loop JOIN { .section}

By default, the Nested Loop JOIN is not enabled for HybridDB for PostgreSQL instances. For queries that only involve or return a small amount of data, the performance may not be optimal.

Take the following SQL statement as an example:

```
select * from T1 join T2 on T1.c1 = T2.c1 where T1.c2 >= '230769548' and T1.c2 < '230769549' limit 100;
```

In this example, the T1 and T2 tables are both big in size. The selection conditions of `T1 (T1.c2 >= ‘230769548’` and `T1.c2 < ‘23432442’)` filter a vast majority of data records and contain LIMIT clauses.

As a result, the query actually involves only a small portion of the total data size. In this case, the Nested Loop JOIN method is optimal.

You can perform the following SET command to activate the Nested Loop JOIN:

```
show enable_nestloop ;
 enable_nestloop
-----------------
 off
SET enable_nestloop = on ;
show enable_nestloop ;
 enable_nestloop
-----------------
 on
explain select * from T1 join T2 on T1.c1 = T2.c1 where T1.c2 >= '230769548' and T1.c2 < '23432442' limit 100;
                                            QUERY PLAN
-----------------------------------------------------------------------------------------------
 Limit  (cost=0.26..16.31 rows=1 width=18608)
   ->  Nested Loop  (cost=0.26..16.31 rows=1 width=18608)
         ->  Index Scan using T1 on c2  (cost=0.12..8.14 rows=1 width=12026)
               Filter: ((c2 >= '230769548'::bpchar) AND (c2 < '230769549'::bpchar))
         ->  Index Scan using T2 on c1  (cost=0.14..8.15 rows=1 width=6582)
               Index Cond: ((c1)::text = (T1.c1)::text)
```

From the query plan, the T1 and T2 tables adopt the Nested Loop JOIN, and achieve the optimal performance.

## Use the ORCA optimizer { .section}

HybridDB for PostgreSQL supports the ORCA optimizer. When you perform a complicated SQL statement and find the unsatisfactory performance, you can try the ORCA optimizer.

You can enable the ORCA by running the following SET command in the database connection.

**Note:** The SET command acts at the connection level and is only valid within the same connection. You need to run the SET command again for a new connection to enable the ORCA.

```
EXPLAIN <SQL text>
SET optimizer = on;
EXPLAIN <SQL text>
```

In the preceding example, you can view that the query plan uses the EXPLAIN command before and after enabling the ORCA respectively. In this way, you can check whether the ORCA has actually changed the SQL query plan.

## Use a compression method { .section}

Now, HybridDB for PostgreSQL supports two compression methods for storage: zlib and RLE.

-   RLE is applicable to the scenario where the same data values are physically stored continuously.
-   Zlib is applicable to other scenarios.

The compression approach can be specified at the field level or table level. For details, see [CREATE TABLE](http://gpdb.docs.pivotal.io/4380/ref_guide/sql_commands/CREATE_TABLE.html).

## Use other numeric types { .section}

If the query contains the unique value statistics operation of COUNT\(DISTINCT\), we recommend that you do not use the string or numeric type for the statistic fields, but try to use other numeric types \(such as integer type\). This method can improve the performance several-fold.

