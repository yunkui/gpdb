# ModifyDBInstanceMaintainTime {#concept_vvs_sbm_q2b .concept}

## Description { .section}

You can call this operation to modify the maintenance window of the instance. Generally, it is set to the periods of off-peak service usage to minimize the impact on services. Alibaba Cloud performs instance maintenance during the maintenance window you set.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to ModifyDBInstanceMaintainTime.|
|DBInstanceId|String|Yes|The ID of the instance.|
|StartTime|String|Yes|The start time of the maintenance window. For example, 02:00Z.|
|EndTime|String|Yes|The end time of the maintenance window. For example, 03:00Z \(the start time should be earlier than the end time\).|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyDBInstanceMaintainTime
&DBInstanceId=gp-xxxxxxx
&StartTime=02:00Z
&EndTime=03:00Z
&<Common request parameters>

```

## Sample responses { .section}

**XML format**

```
<ModifyDBInstanceMaintainTimeResponse>
         <RequestId>CA9A34C8-AC95-413B-AC6A-CEBF67429CCA</RequestId>
</ModifyDBInstanceMaintainTimeResponse>
```

**JSON format**

```
{
   "RequestId": "CA9A34C8-AC95-413B-AC6A-CEBF67429CCA"
}
```

