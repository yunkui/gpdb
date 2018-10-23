# ModifyAccountDescription {#concept_ar4_3cm_q2b .concept}

## Description { .section}

You can call this operation to modify the description of the account so that you can easily identify it.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to ModifyAccountDescription.|
|DBInstanceId|String|Yes|The ID of the instance.|
|AccountName|String|Yes|The name of the account. It must be unique and meet the following requirements:-   Starts with a letter.
-   Contains only lowercase letters, numbers, and underscores.
-   Length constraints: Maximum length of 16 characters.
-   Reserved keywords are not allowed to be used.

|
|AccountDescription|String|Yes|Specifies the name of the account that has been modified. The name must meet the following requirements:-   Starts with a Chinese or English character.
-   Starting with "http://" or "https://" is not allowed.
-   Contains only Chinese characters, English characters, underscores \(\_\), hyphens \(-\), and numbers.
-   Length constraints: Minimum length of 2 characters. Maximum length of 256 characters.

|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyAccountDescription
&DBInstanceId=gp-xxxxxxx
&AccountName=testAccout
&AccountDescription=testAccoutdescribe
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<ModifyAccountDescriptionResponse>
         <RequestId>99BBBD5E-B5D8-4FC8-B8BF-FB1A0A38BBA2</RequestId>
</ModifyAccountDescriptionResponse>
```

**JSON format**

```
{
    "RequestId": "99BBBD5E-B5D8-4FC8-B8BF-FB1A0A38BBA2"
}
```

