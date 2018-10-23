# DescribeDBInstances {#concept_cdm_3bm_q2b .concept}

## Description { .section}

You can call this operation to query the list of instances.

## Request parameters { .section}

|Name|Type|Required| Description|
|----|----|--------|------------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to DescribeDBInstances.|
|RegionId|String| Yes|The name of the region. You can use DescribeRegions to check available regions.|
|Engine| String| No|The database type. Default value: PostgreSQL.|
|DBInstanceType| String|No|The instance type. Valid values:-   Primary: primary instances.
-   Readonly: read-only instances.
-   Guard: disaster recovery instances.
-   Temp: temporary instances.
-   If you do not specify this parameter, instances of all types will be returned.

|
|DBInstanceDescription| String| No|The description of the instance.|
|InstanceNetworkType|String| No|Valid values:-   VPC: VPC network instances.
-   Classic: classic network instances.
-   If you do not specify this parameter, instances of both types will be returned.

|
|ConnectionMode| String| No| -   Standard: standard connection mode.
-   Safe: safe connection mode.
-   If you do not specify this parameter, instances of both modes will be returned.

 |
|Tags|String| No|The name of the tag that is assigned to an instance. It is a JSON string. This string consists of TagKey and TagValue. You must specify a value for TagKey. TagValue is optional. For example, `{"key1":"value1"}`.|
|PageSize|Integer|No|The number of records on each page. Valid values: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|The page number. The value of this parameter is greater than zero and up to the maximum value of an integer. Default value: 1.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|PageNumber|Integer|The number of pages.|
|TotalRecordCount|Integer|The total number of records.|
|PageRecordCount|Integer|The number of instances on the current page.|
|Items|List<DBInstance\>|The list of instances.|

|Name|Type|Description|
|----|----|-----------|
|DBInstanceId|String |The instance name.|
|DBInstanceDescription|String |The description of an instance.|
|PayType|String |The billing method:-   Postpaid: Pay-As-You-Go.
-   Prepaid: Subscription.

|
|InstanceNetworkType|String| -   VPC: VPC network instances
-   Classic: classic network instances

 |
|ConnectionMode|String| -   Standard: standard connection mode
-   Safe: safe connection mode

 |
|RegionId|String|The name of the region.|
|ZoneId|String|zoneId.|
|ExpireTime|String|The expiration time. Pay-As-You-Go instances never expire.|
|DBInstanceStatus|String|For more information, see [Instance statuses](reseller.en-US/API Reference/Appendix/Instance statuses.md#).|
|Engine|String|The database type.|
|EngineVersion|String |The version of a database.|
|DBInstanceNetType|String | -   Internet: a public network
-   Intranet: a private network

 |
|LockMode|String | -   Unlock: a normal state for an instance.
-   ManualLock: An instance is locked manually.
-   LockByExpiration: An instance is locked automatically after the instance expires.
-   LockByRestoration: An instance is locked automatically before a rollback of the instance.
-   LockByDiskQuota: An instance is locked automatically for full disk space.
-   LockReadInstanceByDiskQuota: An instance is read-only for full disk space.

 |
|LockReason|String|The reason for an instance lock.|
|CreateTime|String|The time when you create an instance.|
|VPCId|String|The name of a VPC.|
|VSwitchId|String|The name of a VSwitch.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstances
&RegionId=cn-hangzhou
&<Common request parameters>

```

## Sample responses { .section}

**XML format**

```
<DescribeDBInstancesResponse>
    <Items>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<DBInstanceDescription>gpdb_test</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId>vsw-xxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxx</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2014-10-10T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-27T12:07:11Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType\>Prepaid</PayType\>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<DBInstanceDescription>gp-xxxxxxx</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId>vsw-xxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxx</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-27T11:51:46Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<DBInstanceDescription>test</DBInstanceDescription>
			<InstanceNetworkType>VPC</InstanceNetworkType>
			<VSwitchId>vsw-xxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxx</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2014-10-10T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-27T11:46:11Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Prepaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<ZoneId>cn-hangzhou-f</ZoneId>
			<DBInstanceDescription>Test 2</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId></VSwitchId>
			<VpcId></VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2018-07-20T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-20T05:42:03Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType\>Prepaid</PayType\>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<ZoneId>cn-hangzhou-b</ZoneId>
			<DBInstanceDescription>gp-xxxxxxx</DBInstanceDescription>
			<InstanceNetworkType>vpc</InstanceNetworkType>
			<VSwitchId>vsw-xxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxx</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-03-14T09:15:21Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>5.5</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<ZoneId>cn-hangzhou-d</ZoneId>
			<DBInstanceDescription>Test</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId></VSwitchId>
			<VpcId></VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-05-07T06:48:47Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<ZoneId>cn-hangzhou-b</ZoneId>
			<DBInstanceDescription>gp-xxxxxxx</DBInstanceDescription>
			<InstanceNetworkType>VPC</InstanceNetworkType>
			<VSwitchId>vsw-xxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxx</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-03-16T07:10:03Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
	</Items>
	<PageNumber>1</PageNumber>
	<TotalRecordCount>7</TotalRecordCount>
	<RequestId>BBE00C04-A3E8-4114-881D-0480A72CB92E</RequestId>
	<PageRecordCount>7</PageRecordCount>
</DescribeDBInstancesResponse>
```

**JSON format**

```
{
    "Items":{
        "DBInstance":[
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"1",
                "DBInstanceId":"gp-xxxxxxx",
                "ZoneId":"cn-hangzhou-e",
                "DBInstanceDescription":"gpdb_test",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"vsw-xxxxxxx",
                "VpcId":"vpc-xxxxxxx",
                "Engine":"gpdb",
                "ExpireTime":"2019-06-27T16:00:00Z",
                "CreateTime":"2018-06-27T12:07:11Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid"
            },
            {
                "LockMode": "Unlock",
                "DBInstanceNetType":"1",
                "DBInstanceId":"gp-xxxxxxx",
                "ZoneId":"cn-hangzhou-e",
                "DBInstanceDescription":"gp-xxxxxxx",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"vsw-xxxxxxx",
                "VpcId":"vpc-xxxxxxx",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-06-27T11:51:46Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-xxxxxxx",
                "ZoneId":"cn-hangzhou-e",
                "DBInstanceDescription":"Test",
                "InstanceNetworkType":"VPC",
                "VSwitchId":"vsw-xxxxxxx",
                "VpcId":"vpc-xxxxxxx",
                "Engine":"gpdb",
                "ExpireTime":"2018-07-27T16:00:00Z",
                "CreateTime":"2018-06-27T11:46:11Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"1",
                "DBInstanceId":"gp-xxxxxxx",
                "ZoneId":"cn-hangzhou-f",
                "DBInstanceDescription":"Test 2",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"",
                "VpcId":"",
                "Engine":"gpdb",
                "ExpireTime":"2018-07-20T16:00:00Z",
                "CreateTime":"2018-06-20T05:42:03Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-xxxxxxx",
                "ZoneId":"cn-hangzhou-b",
                "DBInstanceDescription":"gp-xxxxxxx",
                "InstanceNetworkType":"VPC",
                "VSwitchId":"vsw-xxxxxxx",
                "VpcId":"vpc-xxxxxxx",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-06-05T03:42:41Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-xxxxxxx",
                "ZoneId":"cn-hangzhou-b",
                "DBInstanceDescription":"Test",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"",
                "VpcId":"",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-05-07T06:48:47Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-xxxxxxx",
                "ZoneId":"cn-hangzhou-b",
                "DBInstanceDescription":"gp-xxxxxxx",
                "InstanceNetworkType":"VPC",
                "VSwitchId":"vsw-xxxxxxx",
                "VpcId":"vpc-xxxxxxx",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-03-16T07:10:03Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            }
        ]
    },
    "PageNumber":1,
    "TotalRecordCount":7,
    "RequestId":"BBE00C04-A3E8-4114-881D-0480A72CB92E",
    "PageRecordCount":7
}

```

