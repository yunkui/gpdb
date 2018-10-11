# DescribeSQLCollectorPolicy {#concept_xxh_ygm_q2b .concept}

## 描述 { .section}

查询指定实例的SQL采集功能是否打开。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值：DescribeSQLCollectorPolicy。|
|DBInstanceId|String|是|实例名。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|
|SQLCollectorStatus|String| -   Enable：SQL采集开启。
-   Disabled：SQL采集关闭。

 |

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeSQLCollectorPolicy
&DBInstanceId=gp-xxxxxxx
&<公共请求参数>
```

## 返回示例 { .section}

**XML格式**

```
<DescribeSQLCollectorPolicyResponse>
	<RequestId>ABB39CC3-4488-4857-905D-2E4A051D0521</RequestId>
	<SQLCollectorStatus>Enable</SQLCollectorStatus>
</DescribeSQLCollectorPolicyResponse>
```

**JSON格式**

```
{
    "RequestId":"ABB39CC3-4488-4857-905D-2E4A051D0521",
    "SQLCollectorStatus":"Enable"
}
```

