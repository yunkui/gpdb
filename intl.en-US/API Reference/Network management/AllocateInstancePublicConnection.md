# AllocateInstancePublicConnection {#concept_ks2_hhm_q2b .concept}

## Description { .section}

You can call this operation to specify a prefix for the public network connection string of the instance.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to AllocateInstancePublicConnection.|
|DBInstanceId|String|Yes|The instance ID.|
|ConnectionStringPrefix|String| Yes|The prefix of the connection string.|
|Port|String| Yes|The port number. Valid values: 3200 to 3999.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests {#section_mgb_1p5_42b .section}

```
https://gpdb.aliyuncs.com/?Action=AllocateInstancePublicConnection
&DBInstanceId=gp-xxxxxxx
&ConnectionStringPrefix=gp-xxxxxxx
&Port=3432
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<AllocateInstancePublicConnectionResponse>  
     <RequestId>ADD6EA90-EECB-4C12-9F26-0B6DB58710EF</RequestId>
</AllocateInstancePublicConnectionResponse>
```

**JSON format**

```
{
   "RequestId": "ADD6EA90-EECB-4C12-9F26-0B6DB58710EF"
}
```

