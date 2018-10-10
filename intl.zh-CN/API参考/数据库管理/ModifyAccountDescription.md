# ModifyAccountDescription {#concept_ar4_3cm_q2b .concept}

## 描述 { .section}

该接口用于修改数据库名的备注名，用于方便用户记录该实例。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为ModifyAccountDescription。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|操作账号，必须具有唯一性：-   以字母开头；
-   由小写字母，数字、下划线组成；
-   长度不超过16个字符。
-   不得使用数据库系统常用的关键字。

|
|AccountDescription|String|是|修改账号备注：-   以中文、英文字母开头；
-   不能以http://或https://开头
-   可以包含中文、英文字符、“\_”、“ -”、数字；
-   长度为2~256个字符。

|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=ModifyAccountDescription
&DBInstanceId=gp-bp1gjo105888f3b69
&AccountName=testAccout
&AccountDescription=testAccoutdescribe
&<公共请求参数>
```

## 返回示例 { .section}

**XML格式**

```
<ModifyAccountDescriptionResponse>
         <RequestId>99BBBD5E-B5D8-4FC8-B8BF-FB1A0A38BBA2</RequestId>
</ModifyAccountDescriptionResponse>
```

**JSON格式**

```
{
    "RequestId": "99BBBD5E-B5D8-4FC8-B8BF-FB1A0A38BBA2"
}
```

