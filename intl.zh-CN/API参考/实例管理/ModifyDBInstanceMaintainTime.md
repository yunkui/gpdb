# ModifyDBInstanceMaintainTime {#concept_vvs_sbm_q2b .concept}

## 描述 { .section}

该接口用于修改实例的例行可维护时间，一般设置为业务的低峰时段，将维护对业务的影响降到最低。阿里云会在您设置的可维护时段内进行实例维护，

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceMaintainTime。|
|DBInstanceId|String|是|实例名。|
|StartTime|String|是|可运维的开始时间。例如：02:00Z。|
|EndTime|String|是|可运维的结束时间。例如：03:00Z（开始时间应大于结束时间）。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyDBInstanceMaintainTime
&DBInstanceId=gp-bp1gjo105888f3b69
&StartTime=02:00Z
&EndTime=03:00Z
&<公共请求参数>

```

## 返回示例 { .section}

**XML格式**

```
<ModifyDBInstanceMaintainTimeResponse>
         <RequestId>CA9A34C8-AC95-413B-AC6A-CEBF67429CCA</RequestId>
</ModifyDBInstanceMaintainTimeResponse>
```

**JSON格式**

```
{
   "RequestId": "CA9A34C8-AC95-413B-AC6A-CEBF67429CCA"
}
```

