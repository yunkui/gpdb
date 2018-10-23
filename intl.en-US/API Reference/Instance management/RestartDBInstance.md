# RestartDBInstance {#concept_wwg_5bm_q2b .concept}

## Description { .section}

You can call this operation to restart the database instance.

## Parameters { .section}

|**Name**|**Type**|**Required**|**Description**|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to RestartDBInstance.|
|DBInstanceId|String|Yes|The ID of the instance.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=RestartDBInstance
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<RestartDBInstance>
         <RequestId>A7356493-7141-4393-8951-CDA8AB5D67EC</RequestId>
</RestartDBInstance>
```

**JSON format**

```
{
  "RequestId":"A7356493-7141-4393-8951-CDA8AB5D67EC"
}
```

