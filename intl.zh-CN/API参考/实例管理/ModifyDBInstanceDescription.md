# ModifyDBInstanceDescription {#concept_hqr_qbm_q2b .concept}

## 描述 { .section}

该接口用于修改实例的备注名，方便用户记录实例。

**请求参数**

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceDescription。|
|DBInstanceId|String|是|实例名。|
|DBInstanceDescription|Sting|是|实例备注名。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyDBInstanceDescription
&DBInstanceId=gp-bp1gjo105888f3b69
&DBInstanceDescription=testInstanceDescribe
&<公共请求参数>

```

## 返回示例 { .section}

**XML格式**

```
<ModifyDBInstanceDescriptionResponse>
         <RequestId>107BE202-D1A2-479E-98E0-A892B472562F</RequestId>
</ModifyDBInstanceDescriptionResponse>
```

**JSON格式**

```
{
    "RequestId": "107BE202-D1A2-479E-98E0-A892B472562F"
}
```

