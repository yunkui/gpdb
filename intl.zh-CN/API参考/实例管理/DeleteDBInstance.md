# DeleteDBInstance {#concept_u51_fbm_q2b .concept}

## 描述 { .section}

删除实例。

## 输入参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值：DeleteDBInstance。|
|DBInstanceId|String|是|实例名。|

## 返回参数 { .section}

|名称|**类型**|**描述**|
|--|------|------|
|<公共返回参数\>|-|详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=DeleteDBInstance
&DBInstanceId=gp-bp1gjo105888f3b69
&<公共请求参数>

```

## 返回示例 { .section}

**XML格式**

```
<DeleteDBInstanceResponse>  
     <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</DeleteDBInstanceResponse>
```

**JSON格式**

```
{"RequestId":" 65BDA532-28AF-4122-AA39-B382721EEE64"}
```

