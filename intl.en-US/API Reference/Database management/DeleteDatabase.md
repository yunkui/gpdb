# DeleteDatabase {#concept_m11_2cm_q2b .concept}

## Description { .section}

You can call this operation to remove a database of an instance.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request paramters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|The operation that you want to perform. Set the value to DeleteDatabase.|
|DBInstanceId|String| Yes|The instance name.|
|DBName|String| Yes|The database name.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DeleteDatabase
&DBName=testdb01
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

```
<DeleteDatabaseResponse>
     <RequestId>07F6177E-6DE4-408A-BB4F-0723301340F3</RequestId>
</DeleteDatabaseResponse>
```

**JSON format**

```
{
    "RequestId":"07F6177E-6DE4-408A-BB4F-0723301340F3"
 }
```

