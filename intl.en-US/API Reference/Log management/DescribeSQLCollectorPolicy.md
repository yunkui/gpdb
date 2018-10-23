# DescribeSQLCollectorPolicy {#concept_xxh_ygm_q2b .concept}

## Description { .section}

You can call this operation to check whether SQL audit is enabled for the specified instance.

## Request parameters { .section}

|Name|Type|Required| Description|
|----|----|--------|------------|
|<Common request parameters\>|-| Yes|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to DescribeSQLCollectorPolicy.|
|DBInstanceId|String|Yes|The instance ID.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see[Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|SQLCollectorStatus|String| -   Enable: SQL audit is enabled.
-   Disabled: SQL audit is disabled.

 |

## Request example { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeSQLCollectorPolicy
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<DescribeSQLCollectorPolicyResponse>
	<RequestId>ABB39CC3-4488-4857-905D-2E4A051D0521</RequestId>
	<SQLCollectorStatus>Enable</SQLCollectorStatus>
</DescribeSQLCollectorPolicyResponse>
```

**JSON format**

```
{
    "RequestId":"ABB39CC3-4488-4857-905D-2E4A051D0521",
    "SQLCollectorStatus":"Enable"
}
```

