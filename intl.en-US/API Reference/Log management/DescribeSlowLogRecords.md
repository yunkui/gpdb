# DescribeSlowLogRecords {#concept_lxr_wgm_q2b .concept}

## Description { .section}

You can call this operation to query slow query logs of a database in a user instance over a period of time.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request paramters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to DescribeSlowLogRecords.|
|DBInstanceId|String|Yes|The instance name.|
|StartTime|String| Yes|The start time. The format is `YYYY-MM-DDTHH:mmZ`, such as 2011-06-11T15:00Z.|
|EndTime|String|Yes|The end time. The end time is no earlier than the start time. The format is `YYYY-MM-DDTHH:mmZ`, such as 2011-06-11. T16:00Z.|
|SQLId|Long|No|SQL ID.|
|DBName| String|No|The database name.|
|PageSize|Integer|No|The number of records on each page. Valid values: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|The page number. The value of this parameter is greater than zero and up to the maximum value of an integer. Default value: 1.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response paramters\>| |Fore more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|Engine|String|The database type.|
|TotalRecordCount|Interger|The total number of records.|
|PageNumber|Interger|The page number.|
|PageRecordCount|Interger|The number of SQL slow queries on the current page.|
|Items|List<SQLSlowRecord\>|The list of SQLSlowRecord objects.|

|Name|Type|Description|
|----|----|-----------|
|HostAddress|String |The IP address of the client host that you use to connect to a database.|
|DBName|String |The database name.|
|SQLText|String |The SQL statement.|
|QueryTimes|Long|The execution time of the slow query. Unit: seconds.|
|LockTimes|Long|The lock time of the slow query. Unit: seconds.|
|ParseRowCounts|Long|The number of records that a slow query retrieves.|
|ReturnRowCounts|Long|The number of records that a slow query returns.|
|ExecutionStartTime|String|The start time when you execute a query. The format is `YYYY-MM-DDTHH:mm:ss Z`, such as 2011-06-11T15:00:08Z.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeSlowLogRecords
&DBInstanceId=gp-xxxxxxx
&StartTime=2018-07-09T08:00Z
&EndTime=2018-07-09T09:00Z
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<DescribeSlowLogRecordsResponse> 
	<RequestId>542BB8D6-4268-45CC-A557-B03EFD7AB30A</RequestId>
	<Engine>gpdb</Engine>
	<PageNumber>1</PageNumber>
	<PageRecordCount>1</PageRecordCount>
	<TotalRecordCount>1</TotalRecordCount>
	<Items>
		<SQLSlowRecord>
			<HostAddress>127.0.0.1</HostAddress>
			<DBName>test</DBName>
			<SQLText> update test.zxb set id=0 limit 1</SQLText>
			<QueryTimes>123</QueryTimes>
			<LockTimes>12</LockTimes>
			<ParseRowCounts>125</ParseRowCounts>
			<ReturnRowCounts>1</ReturnRowCounts>
			<ExecutionStartTime>2018-07-09T09:00:08Z</ExecutionStartTime>
		</SQLSlowRecord>
	</Items>
</DescribeSlowLogRecordsResponse>
```

**JSON format**

```
{
    "RequestId":"542BB8D6-4268-45CC-A557-B03EFD7AB30A",
    "Engine":"gpdb",
    "PageNumber":1,
    "PageRecordCount":1,
    "TotalRecordCount":1,
    "Items":{
        {"SQLSlowRecord":
            {
                "HostAddress":"127.0.0.1"
                "Name": "test",
                "SQLText":"update test.zxb set id=0 limit 1"
                "QueryTimes":"123",
                "LockTimes":"12",
                "ParseRowCounts":"125",
                "ReturnRowCounts":"1",
                "ExecutionStartTime":"2018-07-09T09:00:08Z"
            }
        ]
    }
}
```

