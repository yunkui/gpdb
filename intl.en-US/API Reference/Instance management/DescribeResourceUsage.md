# DescribeResourceUsage {#concept_uhn_mbm_q2b .concept}

## Description { .section}

You can call this operation to check disk space that is used by an instance.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to DescribeResourceUsage.|
|DBInstanceId|String| Yes|The instance ID.|

## Response parameters { .section}

|Name |Type|Description|
|-----|----|-----------|
|<Common response parameters\>|N/A|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|DBInstanceId|String|The instance ID.|
|Engine|String |The database type.|
|DiskUsed|Integer|The used space of a disk. The used space indicates the user data space \(DataSize\) and log data space \(LogSize\) combined. A value of -1 indicates that this parameter is not applicable. Unit: Bytes.|
|DataSize|Integer|The disk space that is used to store user data. A value of -1 indicates that this parameter is not applicable. Unit: Bytes.|
|LogSize|Integer|The disk space that is used to store log files. A value of -1 indicates that this parameter is not applicable. Unit: Bytes.|
|BackupSize|Integer|The disk space that is used to store backup files. A value of -1 indicates that this parameter is not applicable. Unit: Bytes.|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeResourceUsage
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>

```

## Sample responses { .section}

**XML format**

```
<DescribeResourceUsageResponse>
	<DBInstanceId>gp-xxxxxxx</DBInstanceId>
	<RequestId>860FBA9E-BFFD-493E-91A1-2349B9D74AE7</RequestId>
	<LogSize>201326592</LogSize>
	<DataSize>83886080</DataSize>
	<BackupSize>26624</BackupSize>
	<Engine>gpdb</Engine>
	<DiskUsed>285212672</DiskUsed>
</DescribeResourceUsageResponse>
```

**JSON format**

```
{
    "DBInstanceId":"gp-xxxxxxx",
    "RequestId":"860FBA9E-BFFD-493E-91A1-2349B9D74AE7",
    "LogSize":201326592,
    "DataSize":83886080,
    "BackupSize":26624,
    "Engine":"gpdb",
    "DiskUsed":285212672
}
```

