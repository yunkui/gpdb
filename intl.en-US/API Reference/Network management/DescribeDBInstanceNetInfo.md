# DescribeDBInstanceNetInfo {#concept_qvg_jhm_q2b .concept}

## Description { .section}

You can call this operation to query the connection information of the instance.

## Request parameters { .section}

|Name|Type|Required| Description|
|----|----|--------|------------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to DescribeDBInstanceNetInfo.|
|DBInstanceId|String| Yes|The instance ID.|

## Response parameters { .section}

|Name |Type|Description|
|-----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).,|
|DBInstanceNetInfos|List<DBInstanceNetInfo\>|The connection information of the instance.|
|InstanceNetworkType|String | -   Classic: classic networks.
-   VPC: VPC networks.

 |

|Name|Type|Description|
|----|----|-----------|
|ConnectionString|String |The DNS connection string.|
|IPAddress|String |The IP address.|
|IPType|String | -   For a classic network, the IPType parameter can be Inner or Public.
-   For a VPC network, the IPType parameter can be Private or Public.

 |
|Port|String |The port information.|
|VPCId|String |The name of the VPC.|
|VSwitchId|String|The name of the VSwitch. You can separate multiple values with commas.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstanceNetInfo
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<DescribeDBInstanceNetInfoResponse>
    <instanceNetworkType>Classic</instanceNetworkType>
	<DBInstanceNetInfos>
		<DBInstanceNetInfo>
			<DBInstanceNetType>1</DBInstanceNetType>
			<connectionString>gp-xxxxxxx.gpdb.rds.aliyuncs.com</connectionString>
			<ipAddress>127.0.0.1</ipAddress>
			<port>3432</port>
			<userVisible>1</userVisible>
		</DBInstanceNetInfo>
	</DBInstanceNetInfos>
	<RequestId>7565770E-7C45-462D-BA4A-8A5396F2CAD1</RequestId>
</DescribeDBInstanceNetInfoResponse>
```

**JSON format**

```
{
    "InstanceNetworkType": "classic",
    "DBInstanceNetInfos": {
      "DBInstanceNetInfo": [
        {
           "DBInstanceNetType":"1",
            "connectionString":"gp-xxxxxxx.gpdb.rds.aliyuncs.com",
            "ipAddress":"127.0.0.1",
            "port":"3432",
            "userVisible":1
        }
      ]
    }, 
    "RequestId": "7565770E-7C45-462D-BA4A-8A5396F2CAD1"
  }
```

