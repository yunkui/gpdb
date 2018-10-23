# DescribeSQLLogRecords {#concept_q3g_dhm_q2b .concept}

## Description { .section}

You can call this operation to query SQL audit logs of the instance.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#)。|
|Action|String|Yes|The operation that you want to perform. Set the value to DescribeSQLLogRecords.|
|DBInstanceId|String|Yes|The instance name.|
|Database|String|No|All databases will be queried by default.|
|User|String|No|All users will be checked by default.|
|QueryKeywords|String|No|You can specify keywords for a query. Separate multiple keywords with spaces. The maximum number of keywords is 10.|
|StartTime|String|Yes|The start time. You can query audit logs generated after the specified time. The format is `yyyy-MM-ddTHH:mm:ssZ`.|
|EndTime|String|Yes|The end time. You can query audit logs generated before the specified time. The format is`yyyy-MM-ddTHH:mm:ssZ`. The end time must be no earlier than the start time.|
|PageSize|Integer|No|The number of records on each page. Valid values: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|The page number. The value of this parameter is greater than zero and up to the maximum value of an Integer. Default value: 1.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|TotalRecordCount|Integer|The total number of records.|
|PageNumber|Integer|The page number.|
|PageRecordCount|Interger|The number of SQL log records on the current page.|
|Items|List<SQLRecord\>|None.|

|Name|Type|Description|
|----|----|-----------|
|DBName|String |The database name.|
|AccountName|String|The account name.|
|HostAddress|String|The client IP address.|
|SQLText|String|The SQL statement.|
|TotalExecutionTimes|Long|The execution time of the query. Unit: microseconds.|
|ReturnRowCounts|Long|The number of records returned from the query.|
|ThreadID|String |Thread ID.|
|ExecuteTime|String |The time when you execute the query. The format is `yyyy-MM-ddTHH:mm:ssZ`, such as 2011-05-30. T12:11:20Z.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeSQLLogRecords
&DBInstanceId=gp-xxxxxxx
&StartTime=2018-07-09T04:50:20Z
&EndTime=2018-07-09T08:50:20Z
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<DescribeSQLLogRecordsResponse> 
	<Items></Items>
	<TotalRecordCount>0</TotalRecordCount>
	<PageNumber>1</PageNumber>
	<RequestId>9B24F29F-BA7F-47A3-838E-C6A993888388</RequestId>
	<PageRecordCount>0</PageRecordCount>
</DescribeSQLLogRecordsResponse>
```

**JSON format**

```
{
    "Items":{
        "SQLRecord":[
        ]
    },
    "TotalRecordCount":0,
    "PageNumber":1,
    "RequestId":"9B24F29F-BA7F-47A3-838E-C6A993888388",
    "PageRecordCount":0
}
```

