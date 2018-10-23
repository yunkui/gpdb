# DescribeDBInstanceAttribute {#concept_isw_gbm_q2b .concept}

## Description { .section}

You can call this operation to query the details of an instance.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-| Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to DescribeDBInstanceAttribute.|
|DBInstanceId|String|Yes|The instance ID.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|Items|List<DBInstanceAttribute\>|The list of instance details.|

|Name|Type|Description|
|----|----|-----------|
|AvailabilityValue|String|The service availability of the current instance. Unit: percentage.|
|ConnectionMode|String| -   Performance: standard connection mode
-   Safty: safe connection mode

 |
|ConnectionString|String|The connection string that you can use to connect to a database.|
|CreationTime|String |The time when you create an instance. The format is `YYYY-MM-DDThh:mm:ssZ`, such as 2011-05-30T12:11:4Z.|
|DBInstanceClass|String |The group type.|
|DBInstanceClassType|String |The group type families:-   s: shared instances
-   x: general instances
-   d: dedicated instances
-   h: dedicated hosts \(DDH\)

|
|DBInstanceCpuCores|String|The number of vCPU cores.|
|DBInstanceDescription|String |The description of an instance.|
|DBInstanceDiskMBPS|Long|The maximum disk throughput of a group. Unit: Mbps.|
|DBInstanceGroupCount|String|The number of groups.|
|DBInstanceId|String |The instance ID.|
|DBInstanceMemory|Long|The memory capacity of a group. Unit: MB.|
|DBInstanceNetType|String| -   Internet: the Internet
-   Intranet: a private network

 |
|DBInstanceStatus|String|For more information about the instance status, see [Instance statuses](reseller.en-US/API Reference/Appendix/Instance statuses.md#).|
|DBInstanceStorage|Long|Disk space of an instance. Unit: GB.|
|Engine|String | -   Internet: the Internet
-   Intranet: a private network

 |
|EngineVersion|String |The version of a database.|
|ExpireTime|String|The expiration time of the instance.|
|HostType|String |The disk type of a group.-   0: SSD
-   1: SATA

.|
|InstanceNetworkType|String| -   Classic: classic networks.
-   VPC: VPC networks.

 |
|LockMode|String| -   Unlock: in normal operation
-   ManualLock: locked manually
-   LockByExpiration: locked automatically after the instance expires
-   LockByRestoration: locked automatically before a rollback
-   LockByDiskQuota: locked automatically after the instance space is full

 |
|MaintainEndTime|String|The end time of instance maintenance.|
|MaintainStartTime|String|The start time of instance maintenance.|
|MaxConnections|Integer|The maximum number of concurrent connections to an instance.|
|PayType|String |The billing methods:-   Postpaid: Pay-As-You-Go
-   Prepaid: Subscription

|
|Port|String |The port number that you can use to connect to an instance.|
|RegionId|String |The name of a region.|
|SecurityIPList|String |The whitelist of IP addresses that are allowed to access the instance.|
|VpcId |String |The name of a VPC.|
|ZoneId|String|The name of a zone.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstanceAttribute
&DBInstanceId=gp-xxxxxxx
&<Common request parameter>

```

**Sample responses**

**XML format**

```
<DescribeDBInstanceAttributeResponse>
  <RequestId>B4CAF581-2AC7-41AD-8940-D56DF7AADF5B</RequestId>
  <Items>
    <DBInstanceAttribute>
			<DBInstanceDiskMBPS>300</DBInstanceDiskMBPS>
			<ConnectionString>gp-xxxxxxx.gpdb.rds.aliyuncs.com</ConnectionString>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<ConnectionMode>Performance</ConnectionMode>
			<VpcId>vpc-xxxxxxx</VpcId>
			<Engine>gpdb</Engine>
			<MaxConnections>500</MaxConnections>
			<MaintainStartTime>18:00Z</MaintainStartTime>
			<DBInstanceGroupCount>2</DBInstanceGroupCount>
			<HostType>0</HostType>
			<DBInstanceMemory>16384</DBInstanceMemory>
			<EngineVersion>4.3</EngineVersion>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Prepaid</PayType>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<MaintainEndTime>22:00Z</MaintainEndTime>
			<DBInstanceClass>gpdb.group.segsdx2</DBInstanceClass>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<DBInstanceClassType>x</DBInstanceClassType>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<DBInstanceDescription>gp-xxxxxxx</DBInstanceDescription>
			<DBInstanceStorage>160</DBInstanceStorage>
			<CreationTime>2018-06-27T12:07:10Z</CreationTime>
			<Port>3432</Port>
			<ExpireTime>2019-06-27T16:00:00Z</ExpireTime>
			<RegionId>cn-hangzhou</RegionId>
			<AvailabilityValue>100.0%</AvailabilityValue>
			<DBInstanceCpuCores>2</DBInstanceCpuCores>
			<SecurityIPList>127.0.0.1</SecurityIPList>
    </DBInstanceAttribute>
  </Items>
</DescribeDBInstanceAttributeResponse>
```

**JSON format**

```
{
    "Items":{
        "DBInstanceAttribute":[
            {
                "DBInstanceDiskMBPS":300,
                "ConnectionString":"gp-xxxxxxx.gpdb.rds.aliyuncs.com",
                "ZoneId":"cn-hangzhou-e",
                "ConnectionMode":"Performance",
                "VpcId":"vpc-xxxxxxx",
                "Engine":"gpdb",
                "MaxConnections":500,
                "MaintainStartTime":"18:00Z",
                "DBInstanceGroupCount":"2",
                "HostType":"0",
                "DBInstanceMemory":16384,
                "EngineVersion":"4.3",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid",
                "LockMode":"Unlock",
                "DBInstanceNetType":"1",
                "MaintainEndTime":"22:00Z",
                "DBInstanceClass":"gpdb.group.segsdx2",
                "DBInstanceId":"gp-xxxxxxx",
                "DBInstanceClassType":"x",
                "InstanceNetworkType":"Classic",
                "DBInstanceDescription":"gp-xxxxxxx",
                "DBInstanceStorage":160,
                "CreationTime":"2018-06-27T12:07:10Z",
                "Port":"3432",
                "ExpireTime": "2014-10-10T16:00:00Z",
                "RegionId":"cn-hangzhou",
                "AvailabilityValue":"100.0%",
                "DBInstanceCpuCores":2,
                "SecurityIPList":"127.0.0.1"
            }
        ]
    },
    "RequestId":"B4CAF581-2AC7-41AD-8940-D56DF7AADF5B"
}
```

