# ModifyDBInstanceConnectionMode {#concept_e14_4bm_q2b .concept}

## Description { .section}

You can call this operation to modify the access mode of the instance. Currently, two modes are supported:

-   Standard mode
-   Safe mode

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-| Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to ModifyDBInstanceConnectionMode.|
|DBInstanceId|String|Yes|The ID of the instance.|
|ConnectionMode|String|Yes| -   Standard
-   Safe

 |

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyDBInstanceConnectionMode
&DBInstanceId=gp-xxxxxxx
&ConnectionMode=Safe
&<Common request parameters>

```

## Sample responses { .section}

**XML format**

```
<BaseResponse> 
	<RequestId>8361E350-4CCC-4D28-B020-55B4DCB75D3B</RequestId>
</BaseResponse>
```

**JSON format**

```
{
    "RequestId":"8361E350-4CCC-4D28-B020-55B4DCB75D3B",
}
```

