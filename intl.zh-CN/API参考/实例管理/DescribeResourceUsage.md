# DescribeResourceUsage {#concept_uhn_mbm_q2b .concept}

## 描述 { .section}

查看实例的资源利用情况，返回用户的某个实例的已用空间大小。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值：DescribeResourceUsage。|
|DBInstanceId|String|是|实例名。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|
|DBInstanceId|String|实例名。|
|Engine|String|数据库类型。|
|DiskUsed|Integer|已用空间（DataSize+LogSize），单位：Byte，-1表示没有数据。|
|DataSize|Integer|数据文件占用空间，单位：Byte，-1表示没有数据。|
|LogSize|Integer|日志占用空间，单位：Byte，-1表示没有数据。|
|BackupSize|Integer|备份占用空间，单位：Byte，-1表示没有数据。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeResourceUsage
&DBInstanceId=gp-xxxxxxx
&<公共请求参数>

```

## 返回示例 { .section}

**XML格式**

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

**JSON格式**

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

