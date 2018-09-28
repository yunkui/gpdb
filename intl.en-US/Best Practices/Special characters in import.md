# Special characters in import {#concept_uv4_gvf_v2b .concept}

HybridDB for PostgreSQL supports multiple data importing methods:

-   [Import and export data in parallel by using OSS](../../../../reseller.en-US/Quick Start/Import data/Parallel import from OSS or export to OSS.md#)
-   [Import data from MySQL](../../../../reseller.en-US/Quick Start/Import data/Import data from MySQL.md#)
-   [Import data from PostgreSQL](../../../../reseller.en-US/Quick Start/Import data/Import data from PostgreSQL.md#)
-   [Import data by using the COPY command](../../../../reseller.en-US/Quick Start/Import data/Import data by using the Copy command.md#)
-   [Synchronize data by using Data Integration](../../../../reseller.en-US/Quick Start/Import data/Use Data Integration to synchronize data.md#)

Special characters often cause import failures during data imports. This document describes how to pre-process special characters in the imported data in advance to eliminate problems arising thereof.

In the aforementioned import methods, tools used for importing data from MySQL and PostgreSQL automatically escape and package the special characters, so you can directly use the tools without any additional setting. The following content focuses on using OSS and the COPY command to import data and describes how to process the special characters.

## Import data in parallel by using OSS { .section}

During data import, every line in a file are often regarded as a tuple, and the data in each column are divided by specifying a delimiter in each line. The following content introduces the usage and constraints of the delimiter, and how to handle the special characters in each column.

**Delimiter**

In the syntax of creating an OSS external table, you can specify a DELIMITER after the FORMAT clause as follows:

```
FORMAT 'TEXT' (DELIMITER ',')
```

-   For `FORMAT 'TEXT'`, `DELIMITER` is `'\t'` by default.
-   For `FORMAT 'CSV'`, `DELIMITER` is `','` by default.

You can also define your own delimiter, on the premise that the custom delimiter meets the following constraints, as stipulated in the external table creation syntax:

-   It must be an ASCII character, and must not be a Chinese character, or two or more ASCII characters.
-   `'\n'`and `'\r'` are not supported.
-   Escape characters except `'\n'`and `'\r'` are supported, with "E" or "e" added preceding the character.
-   The escape character `'\t'` with no "E" added is also supported.
-   For the TEXT format, you can set the DELIMITER to OFF and use the single-column external tables.

To read data properly, the content of the OSS file you provide must strictly abide by the delimiter you set.

**Special characters in the data**

During data imports, the use cases where may see special characters include the following:

-   The column contains the same character as the delimiter.

    -   If you are using the TEXT format, you must add an ESCAPE character before each DELIMITER. The ESCAPE character can be specified by using the following command when you create an external table. The default value is the backslash \(\\\).

        ```
        FORMAT 'TEXT' (ESCAPE '\' )
        ```

    -   If you are using the CSV format, you must add double quotation marks \("\) before each DELIMITER.

-   The column contains Chinese characters. OSS external table supports Chinese character data. But to make sure the display is correct, you must encode the created external table as follows:

    ```
    ENCODING 'UTF8'
    ```

-   The column contains null data. You can set to match null values to a character, and replace the specified character with null during data imports. For the CSV format, the default value is a null value with no quotation marks. For the TEXT format, the default value is "\\N". The following command maps space to null. If the column is a space, then the value for the column is null in the data imported from the OSS file.

    ```
    FORMAT 'text' (null ' ' )
    ```

-   The column contains escape characters. You can add "ESCAPE" before the escape characters. The ESCAPE value is specified during external table creation. For CSV format, the default value is the double quotation marks \("\). For TEXT format, the default value is the backslash \(\\\).

    -   You can customize the ESCAPE value to a single character. For example, the following command sets the ESCAPE value to a backslash:

        ```
        FORMAT 'csv' (ESCAPE '\' )
        ```

    -   You can also set ESCAPE to OFF to avoid escaping all characters automatically.

-   The column contains single quotation marks or double quotation marks.

    -   If you are using the TEXT format, you must add an ESCAPE character before the single quotation marks or double quotation marks. The default value is a backslash \(\\\).

    -   If you are using the CSV format, you must add an ESCAPE character before the single quotation marks or double quotation marks. The default value is double quotation marks \("\). You also must add the double quotation marks at both the beginning and end of the column to enclose the column in the quotation marks.


## Import date by using the COPY command { .section}

When you use \\COPY statements to import data, the usage of delimiter is the same as that for using OSS to import data. The handling of special characters in the data is also similar.

The difference is that COPY statements and the `CREATE EXTERNAL TABLE` statement are slightly different in usage. For more information, see [Import data by using the COPY command](../../../../reseller.en-US/Quick Start/Import data/Import data by using the Copy command.md#).

