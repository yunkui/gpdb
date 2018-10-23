# ResetAccountPassword {#concept_m3l_ncm_q2b .concept}

## Description { .section}

You can call this operation to reset the password for your account. The prerequisites are as follows.

-   The instance is running.
-   The instance is not locked.

## Parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to ResetAccountPassword.|
|DBInstanceId|String|Yes|The ID of the instance.|
|AccountName|String| Yes|The name of the account.|
|AccountPassword|String| Yes|The new password consists of at least three types of characters of uppercase letters, lowercase letters, numbers, and special characters. The special character is "!". Length constraints: Minimum length of 8 characters. Maximum length of 32 characters. @\#$%^&\*\(\)\_+-=。|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=ResetAccountPassword
&AccountName=testaccount_1
&AccountPassword=Testaccount_1
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<ResetAccountPasswordResponse>
         <RequestId>187C80FC-75C4-477C-BBF2-A368A36D041C</RequestId>
</ResetAccountPasswordResponse>
```

**JSON format**

```
{
    "RequestId":"187C80FC-75C4-477C-BBF2-A368A36D041C"
}
```

