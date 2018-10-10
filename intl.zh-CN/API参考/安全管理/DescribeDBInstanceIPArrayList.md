# DescribeDBInstanceIPArrayList {#concept_h1y_sgm_q2b .concept}

## 描述 { .section}

查询允许访问实例的IP名单。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为DescribeDBInstanceIPArrayList。|
|DBInstanceId|String|是|实例名。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|
|Items|List<DBInstanceIPArray\>|实例的IP白名单分组列表。|

|名称|类型|描述|
|--|--|--|
|DBInstanceIPArrayName|String|IP白名单分组的名字。|
|DBInstanceIPArrayAttribute|String|默认为空。用以区分不同的属性值，控制台不显示带有`hidden`属性的分组。|
|SecurityIPList|String|IP白名单分组下的IP列表，最多1000个以逗号隔开，有以下三种格式：-   0.0.0.0/0；
-   10.23.12.24（IP）；
-   10.23.12.24/24（CIDR模式，无类域间路由，/24表示了地址中前缀的长度，范围为\[1,32\]）。

|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstanceIPArrayList
&DBInstanceId=gp-bp1gjo105888f3b69
&<公共请求参数>
```

## 返回示例 { .section}

**XML格式**

```
<DescribeDBInstanceIPArrayListResponse>
  <RequestId>CB7AA0BF-BE41-480E-A3DC-C97BF85A391B</RequestId>
  <Items>
    <DBInstanceIPArray>
        <groupName>default</groupName>
		 <groupTag></groupTag>
		 <securityIPList>127.0.0.1</securityIPList>
    </DBInstanceIPArray>
</DescribeDBInstanceIPArrayListResponse>
```

**JSON格式**

```
{
    "Items":{
        "DBInstanceIPArray":[
            {
              "groupName":"default",
              "groupTag":"",
              "securityIPList":"127.0.0.1"
            }
        ]
    },
    "RequestId":"CB7AA0BF-BE41-480E-A3DC-C97BF85A391B"
}
```

