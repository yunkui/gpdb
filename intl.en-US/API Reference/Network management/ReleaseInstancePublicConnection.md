# ReleaseInstancePublicConnection {#concept_tmj_qhm_q2b .concept}

## Description { .section}

You can call this operation to release the public network connection string of the instance.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to ReleaseInstancePublicConnection.|
|DBInstanceId|String|Yes|The ID of the instance.|
|CurrentConnectionString|String|Yes|The public network connection string of the instance.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=ReleaseInstancePublicConnection
&DBInstanceId=gp-xxxxxxx
&CurrentConnectionString=gp-xxxxxxx.gpdb.rds.aliyuncs.com
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<ReleaseInstancePublicConnectionResponse>  
         <RequestId>9CEF7037-4158-4A65-BEC7-2A1541F6FE74</RequestId>
</ReleaseInstancePublicConnectionResponse>
```

**JSON format**

```
{
   "RequestId": "9CEF7037-4158-4A65-BEC7-2A1541F6FE74"
}
```

