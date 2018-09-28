# How to clear the data on a locked disk? {#concept_grh_d3g_v2b .concept}

## Analysis { .section}

When the disk space of any computing group reaches the limit or the disk space on a master node reaches the limit, the entire instance is locked. Connect to the database and run the following command to check whether your instance is locked:

```
show rds_force_trans_ro_non_sup;
```

If the `rds_force_trans_ro_non_sup` value is `on` in the response, it means that the instance is locked, and the database is read-only.

## Fix { .section}

When an instance is locked because the disk is full, the **truncate, drop, and grant** operations are still supported on the data table. You can use these operations to clear the disk until the space falls within the threshold. After that, the instance is automatically unlocked in about five minutes.

**Note:** Deletion is not supported when the instance is locked. Because deletion requests writing data to the xlog, which can increase space usage.

You can also run the following statement to query the table size:

```
select pg_size_pretty(pg_total_relation_size('test'));
```

