# ModifyDBInstanceConnectionString {#concept_ryv_khm_q2b .concept}

## Description { .section}

You can call this operation to modify the connection string and the port.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to ModifyDBInstanceConnectionString.|
|DBInstanceId|String|Yes|The ID of the instance.|
|CurrentConnectionString|String| Yes|The current connection string of the instance.|
|ConnectionStringPrefix|String| Yes|The target connection string.|
|Port|String|No|The target port.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyDBInstanceConnectionString
&DBInstanceId=gp-xxxxxxx
&CurrentConnectionString=gp-xxxxxxx.gpdb.rds.aliyuncs.com
&ConnectionStringPrefix=gp-xxxxxxxnew
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<ModifyDBInstanceConnectionStringResponse>
         <RequestId>29B0BF34-D069-4495-92C7-FA6D94528A9E</RequestId>
</ModifyDBInstanceConnectionStringResponse>
```

**JSON format**

```
{
      "RequestId":"29B0BF34-D069-4495-92C7-FA6D94528A9E"
  }
```

