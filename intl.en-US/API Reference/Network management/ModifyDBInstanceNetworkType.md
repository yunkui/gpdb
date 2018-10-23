# ModifyDBInstanceNetworkType {#concept_ofq_mhm_q2b .concept}

## Description { .section}

You can call this operation to switch the network type of the instance between a VPC and a classic network.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to ModifyDBInstanceNetworkType.|
|DBInstanceId|String|Yes|The ID of the instance.|
|InstanceNetworkType|String|Yes|The type of the network:-   VPC
-   Classic

|
|VPCId| String| No|The ID of the VPC.|
|VSwitchId|String|No|The ID of the VSwitch. This parameter is required if the value of VPCId is specified.|
|PrivateIpAddress|String|No|You can specify the IP address of the VPC to which the VSwitch belongs. If no IP address is specified, the system automatically assigns one IP address based on the VPCId and VSwitchId.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyDBInstanceNetworkType
&DBInstanceId=gp-xxxxxxx
&InstanceNetworkType=VPC
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<ModifyDBInstanceNetworkTypeResponse>
         <RequestId>2d0c35a9-f5da-44ba-852d-741e27b7eb0b</RequestId>
</ModifyDBInstanceNetworkTypeResponse>
```

**JSON format**

```
{
  "RequestId":"2d0c35a9-f5da-44ba-852d-741e27b7eb0b"
}
```

