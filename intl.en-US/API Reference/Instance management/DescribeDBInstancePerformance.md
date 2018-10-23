# DescribeDBInstancePerformance {#concept_asc_ccm_q2b .concept}

## Description { .section}

You can call this operation to check the list of database performance metrics for an instance over a period of time.

## Request parameters { .section}

|Name|Type|Required| Description|
|----|----|--------|------------|
|<Common request parameters\>|-| Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to DescribeDBInstancePerformance.|
|DBInstanceId|String| Yes|The instance name.|
|Key|String| Yes|Metrics of database performance. Separate multiple metrics with commas. For more information, see [Performance parameters](reseller.en-US/API Reference/Appendix/Performance parameters.md#)。|
|StartTime|String| Yes|The start time of a period during which you want to check metrics. For example, 2018-06-11T15:00Z.|
|EndTime|String| Yes|The end time of a period during which you want to check metrics. For example, 2018-06-11T16:00Z.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response paramters\>|None.|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb)。|
|DBInstanceId|String |The instance name.|
|Engine|String |The database type.|
|StartTime|String|The start time. The format is `YYYY-MM-DDTHH:mmZ`, such as 2018-05-30T03:29Z.|
|EndTime|String|The end time. The end time must not be earlier than the start time. The format is `YYYY-MM-DDTHH:mmZ`, such as 2018-05-30T03:29Z.|
|PerformanceKeys|List<PerformanceKey\>|List of metrics, such as \{perf1, perf2, perf3, …\}.|

|Name|Type|Description|
|----|----|-----------|
|Key|String |The name of a metric.|
|Unit|String |The unit of a metric.|
|ValueFormat|String |The format of a value: If multiple metrics return in the value of this parameter, these metrics will be separated with ampersands \(&\), such as `com_delete&com_insert&com_insert_select&com_replace`.

|
|GroupValues|List<GroupValue\>|List of group values, such as \{value1, value2, …\}.|

|Name|Type|Description|
|----|----|-----------|
|Name|String |The group name.|
|Values|List<Value\>|List of values, such as \{value1, value2, …\}.|

|Name|Type|Description|
|----|----|-----------|
|Value|String |The value of a metric.|
|date|String|The time when the metric value was recorded.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstancePerformance
&DBInstanceId=gp-xxxxxxx
&key=CpuUsage,MemoryUsage,Gpdb_SpaceUsage,Gpdb_IOPS,Gpdb_session
& Endtime = MAID: 00Z
&StartTime=2015-11-30T01:33Z
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<DescribeDBInstancePerformanceResponse> 
    <RequestId>5E85244A-AB47-46A3-A3AD-5F307DCB407E</RequestId>
	<DBInstanceId>gp-xxxxxxx</DBInstanceId>
	<PerformanceKeys>
		<Key>MemoryUsage</Key>
		<GroupValues>
			<Name>7198315-1530522046144-1</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Name>7198315-1530522046144-0</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Values />
			<Name>master</Name>
		</GroupValues>
		<Unit>%</Unit>
		<ValueFormat>mem_usage</ValueFormat>
	</PerformanceKeys>
	<PerformanceKeys>
		<Key>Gpdb_session</Key>
		<GroupValues>
			<Name>7198315-1530522046144-1</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Name>7198315-1530522046144-0</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Values />
			<Name>master</Name>
		</GroupValues>
		<Unit>int</Unit>
		<ValueFormat>conn_count</ValueFormat>
	</PerformanceKeys>
	<PerformanceKeys>
		<Key>CpuUsage</Key>
		<GroupValues>
			<Name>7198315-1530522046144-1</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Name>7198315-1530522046144-0</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Values />
			<Name>master</Name>
		</GroupValues>
		<Unit>%</Unit>
		<ValueFormat>cpu_usage</ValueFormat>
	</PerformanceKeys>
	<PerformanceKeys>
		<Key>Gpdb_IOPS</Key>
		<GroupValues>
			<Name>7198315-1530522046144-1</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Name>7198315-1530522046144-0</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Values />
			<Name>master</Name>
		</GroupValues>
		<Unit>int</Unit>
		<ValueFormat>data_iops&write_iops&read_iops</ValueFormat>
	</PerformanceKeys>
	<PerformanceKeys>
		<Key>Gpdb_SpaceUsage</Key>
		<GroupValues>
			<Name>7198315-1530522046144-1</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Name>7198315-1530522046144-0</Name>
			<Values />
		</GroupValues>
		<GroupValues>
			<Values />
			<Name>master</Name>
		</GroupValues>
		<Unit>Byte</Unit>
		<ValueFormat>space</ValueFormat>
	</PerformanceKeys>
	<EndTime>2018-07-09T03:47Z</EndTime>
	<StartTime>2018-07-08T03:47Z</StartTime>
	<Engine>gpdb</Engine>
</DescribeDBInstancePerformanceResponse>
```

**JSON format**

```
{
        "RequestId":"5E85244A-AB47-46A3-A3AD-5F307DCB407E",
        "DBInstanceId":"gp-xxxxxxx",
        "PerformanceKeys":[
            {
                "Key":"MemoryUsage",
                "GroupValues":[
                    {
                        "Name":"7198315-1530522046144-1",
                        "Values":Array[288]
                    },
                    {
                        "Name":"7198315-1530522046144-0",
                        "Values":Array[288]
                    },
                    {
                        "Values":Array[288],
                        "Name":"master"
                    }
                ],
                "Unit":"%",
                "ValueFormat":"mem_usage"
            },
            {
                "Key":"Gpdb_session",
                "GroupValues":[
                    {
                        "Name":"7198315-1530522046144-1",
                        "Values":Array[288]
                    },
                    {
                        "Name":"7198315-1530522046144-0",
                        "Values":Array[288]
                    },
                    {
                        "Values":Array[288],
                        "Name":"master"
                    }
                ],
                "Unit":"int",
                "ValueFormat":"conn_count"
            },
            {
                "Key":"CpuUsage",
                "GroupValues":[
                    {
                        "Name":"7198315-1530522046144-1",
                        "Values":Array[288]
                    },
                    {
                        "Name":"7198315-1530522046144-0",
                        "Values":Array[288]
                    },
                    {
                        "Values":Array[288],
                        "Name":"master"
                    }
                ],
                "Unit":"%",
                "ValueFormat":"cpu_usage"
            },
            {
                "Key":"Gpdb_IOPS",
                "GroupValues":[
                    {
                        "Name":"7198315-1530522046144-1",
                        "Values":Array[288]
                    },
                    {
                        "Name":"7198315-1530522046144-0",
                        "Values":Array[288]
                    },
                    {
                        "Values":Array[288],
                        "Name":"master"
                    }
                ],
                "Unit":"int",
                "ValueFormat":"data_iops&write_iops&read_iops"
            },
            {
                "Key":"Gpdb_SpaceUsage",
                "GroupValues":[
                    {
                        "Name":"7198315-1530522046144-1",
                        "Values":Array[288]
                    },
                    {
                        "Name":"7198315-1530522046144-0",
                        "Values":Array[288]
                    },
                    {
                        "Values":Array[288],
                        "Name":"master"
                    }
                ],
                "Unit":"Byte",
                "ValueFormat":"space"
            }
        ],
        "EndTime":"2018-07-09T03:47Z",
        "StartTime":"2018-07-08T03:47Z",
        "Engine":"gpdb"
    }

```

