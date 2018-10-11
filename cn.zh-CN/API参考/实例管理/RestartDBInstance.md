# RestartDBInstance {#concept_wwg_5bm_q2b .concept}

## 描述 { .section}

重启数据库实例。

## 输入参数 { .section}

|**名称**|**类型**|**是否必须**|**描述**|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值：RestartDBInstance。|
|DBInstanceId|String|是|实例名。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=RestartDBInstance
&DBInstanceId=gp-xxxxxxx
&<公共请求参数>
```

## 返回示例 { .section}

**XML格式**

```
<RestartDBInstance>
         <RequestId>A7356493-7141-4393-8951-CDA8AB5D67EC</RequestId>
</RestartDBInstance>
```

**JSON格式**

```
{
  "RequestId":"A7356493-7141-4393-8951-CDA8AB5D67EC"
}
```

