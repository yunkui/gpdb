# CreateAccount {#concept_i4v_lcm_q2b .concept}

## Description { .section}

You can call this operation to create an account for a database.

## Request parameters { .section}

|Name|Type|Required| Description|
|----|----|--------|------------|
|<Common request parameters\>|-| Yes|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to CreateAccount.|
|DBInstanceId|String| Yes|The instance name.|
|DatabaseName|String|No|The database name.|
|AccountName|String|Yes|The account name.|
|AccountPassword|String| Yes|The password.|
|AccountDescription| String| No|The description of the account.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=CreateAccount
&AccountName=testacc02
&AccountPassword=pw1234
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<CreateAccountResponse>
         <RequestId>D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD</RequestId>
</CreateAccountResponse>
```

**JSON format**

```
{
  "RequestId":"D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD"
}
```

