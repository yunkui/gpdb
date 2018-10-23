# DescribeSQLLogFiles {#concept_tgk_bhm_q2b .concept}

## Description { .section}

You can call this operation to query the list of audit log files.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to DescribeSQLLogFiles.|
|DBInstanceId|String| Yes|The instance name.|
|FileName| String|No|The file name.|
|PageSize |Integer|No|The number of records on each page. Valid values: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|The page number. The value of the parameter is greater than zero and up to the maximum value of an integer. Default value: 1.|

## Response parameters { .section}

|Name |Type|Description|
|-----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|TotalRecordCount|Interger|The total number of records.|
|PageNumber|Interger|The page number.|
|PageRecordCount|Integer|The number of records on the current page.|
|Items|List<LogFile\>|The list of the audit log files.|

|Name|Type|Description|
|----|----|-----------|
|FileID|Integer|The name of an audit log file.|
|LogStatus|String | -   NoStart: The database has not started generating audit log files.
-   Generating: The database is generating audit log files.
-   Success: The database has generated audit log files.
-   Failed: The database fails to generate audit log files.

 |
|LogStartTime|String |The time when an audit log starts to record data.|
|LogEndTime|String |The time when an audit log stops to record data.|
|LogDownloadURL|String |The download URL of audit log files. If the download URL is unavailable, this parameter will be empty.|
|LogSize|Long|The size of an audit log file. Unit: bytes.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeSQLLogFiles
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<DescribeSQLLogFilesResponse> 
	<Items></Items>
	<PageNumber>1</PageNumber>
	<TotalRecordCount>0</TotalRecordCount>
	<RequestId>66E164C1-D7F2-4D85-849D-E2883FCFFBA5</RequestId>
	<PageRecordCount>0</PageRecordCount>
</DescribeSQLLogFilesResponse>
```

**JSON format**

```
{
    "Items": {
        "LogFile":[

        ]
    },
    "PageNumber":1,
    "TotalRecordCount":0,
    "RequestId":"66E164C1-D7F2-4D85-849D-E2883FCFFBA5",
    "PageRecordCount":1
}

```

