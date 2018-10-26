# Enable SQL audit {#concept_ezs_5gf_hfb .concept}

HybridDB for PostgreSQL provides the SQL audit function for you to view SQL details and take a periodic audit of your SQL activity. Enabling SQL audit does not affect the instance performance.

## Background information { .section}

SQL audit records all DML and DDL operations. The system captures such operations by analyzing data transmitted through network protocols. Some of the operations may be missed when a large volume of SQL queries are sent to the database instance.

## Note { .section}

-   SQL audit records are saved for 30 days.
-   By default, the SQL audit function is disabled for instances.

## Procedure { .section}

1.  Log on to the [HybridDB for PostgreSQL console](https://partners-intl.console.aliyun.com/#/gpdb).
2.  Select the **Region** of the instance.
3.  Locate the target instance. In the Actions column, click **Manage**.
4.  In the left-side navigation pane, click **Security Controls**.
5.  Select the SQL Audit tab, and click **Enable SQL Audit Log**.
6.  In the dialog box that appears, click **Confirm** to enable the SQL audit function.
    -   After enabling SQL Audit, you can query SQL information using criteria, such as **Select time range**, **DB**, **User**, and **Keyword**.
    -   To disable the SQL audit function, click the **Disable SQL Audit Log** button on the SQL Audit tab page.

