# DescribeDBInstances {#concept_cdm_3bm_q2b .concept}

## 描述 { .section}

描述数据库实例列表。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为DescribeDBInstances。|
|RegionId|String|是|实例的region，通过接口DescribeRegions查看。|
|Engine|String|否|数据库类型，默认取值为PostgreSQL。|
|DBInstanceType|String|否|实例类型，取值范围如下：-   Primary：主实例
-   Readonly：只读实例
-   Guard：灾备实例
-   Temp：临时实例
-   不填：默认返回所有。

|
|DBInstanceDescription|String|否|实例描述。|
|InstanceNetworkType|String|否|返回指定网络类型的实例，取值范围如下：-   VPC：专有网络类型
-   Classic：经典网络类型
-   不填：默认返回所有网络类型的实例。

|
|ConnectionMode|String|否| -   Standard：为标准访问模式。
-   Safe：为高安全访问模式。
-   不填：默认返回所有。

 |
|Tags|String|否|查询绑定该标签的实例，传入值格式为JSON string，包括TagKey和TagValue，TagKey不能为空，TagValue可为空。格式示例：`{"key1":"value1"}`。|
|PageSize|Integer|否|每页记录数，取值：30/50/100，默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值，默认值：1。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|
|PageNumber|Integer|页数|
|TotalRecordCount|Integer|总记录数。|
|PageRecordCount|Integer|本页实例个数。|
|Items|List<DBInstance\>|由DBInstance组成的数组。|

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例名。|
|DBInstanceDescription|String|实例描述。|
|PayType|String|付费类型：-   Postpaid：按量付费。
-   Prepaid：包年包月。

|
|InstanceNetworkType|String|网络类型：-   VPC：专有网络类型
-   Classic：经典网络类型

|
|ConnectionMode|String| -   Standard：标准访问模式
-   Safe：高安全访问模式

 |
|RegionId|String|地域。|
|ZoneId|String|可用区。|
|ExpireTime|String|到期时间，按量付费实例无到期时间。|
|DBInstanceStatus|String|详见[实例状态表](intl.zh-CN/API参考/附录/实例状态表.md#)。|
|Engine|String|数据库类型。|
|EngineVersion|String|数据库版本。|
|DBInstanceNetType|String| -   Internet：外网
-   Intranet：内网

 |
|LockMode|String| -   Unlock：正常
-   ManualLock：手动触发锁定
-   LockByExpiration：实例过期自动锁定
-   LockByRestoration：实例回滚前的自动锁定
-   LockByDiskQuota：实例空间满自动锁定，不可访问实例
-   
 |
|LockReason|String|被锁定的原因。|
|CreateTime|String|创建时间。|
|VPCId|String|VPC ID。|
|VSwitchId|String|VSwitch ID。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstances
&RegionId=cn-hangzhou
&<公共请求参数>

```

## 返回示例 { .section}

**XML格式**

```
<DescribeDBInstancesResponse>
    <Items>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<DBInstanceId>gp-bp1gjo105888f3b69</DBInstanceId>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<DBInstanceDescription>gpdb_test</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId>vsw-bp13jjr8p2cq6oliv305m</VSwitchId>
			<VpcId>vpc-bp1jjr367nag22y0ywvj6</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2019-06-27T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-27T12:07:11Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType\>Prepaid</PayType\>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<DBInstanceId>gp-bp1d2340z5yx6xzhg</DBInstanceId>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<DBInstanceDescription>gp-bp1d2340z5yx6xzhg</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId>vsw-bp13jjr8p2cq6oliv305m</VSwitchId>
			<VpcId>vpc-bp1jjr367nag22y0ywvj6</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-27T11:51:46Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-bp1lugtm4dn30mg1f</DBInstanceId>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<DBInstanceDescription>测试</DBInstanceDescription>
			<InstanceNetworkType>VPC</InstanceNetworkType>
			<VSwitchId>vsw-bp13jjr8p2cq6oliv305m</VSwitchId>
			<VpcId>vpc-bp1jjr367nag22y0ywvj6</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2018-07-27T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-27T11:46:11Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Prepaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<DBInstanceId>gp-bp16511m0e6km530g</DBInstanceId>
			<ZoneId>cn-hangzhou-f</ZoneId>
			<DBInstanceDescription>测试2</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId></VSwitchId>
			<VpcId></VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2018-07-20T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-20T05:42:03Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType\>Prepaid</PayType\>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-bp1xm5o26k5tx08j2</DBInstanceId>
			<ZoneId>cn-hangzhou-b</ZoneId>
			<DBInstanceDescription>gp-bp1xm5o26k5tx08j2</DBInstanceDescription>
			<InstanceNetworkType>VPC</InstanceNetworkType>
			<VSwitchId>vsw-bp1e55m105fuxg5coy41p</VSwitchId>
			<VpcId>vpc-bp1gvpfymsw2t8cv4o297</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-06-05T03:42:41Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-bp1g60zau80mxt9cr</DBInstanceId>
			<ZoneId>cn-hangzhou-b</ZoneId>
			<DBInstanceDescription>测试</DBInstanceDescription>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<VSwitchId></VSwitchId>
			<VpcId></VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-05-07T06:48:47Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
		<DBInstance>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>2</DBInstanceNetType>
			<DBInstanceId>gp-bp1408002b6mf7fo9</DBInstanceId>
			<ZoneId>cn-hangzhou-b</ZoneId>
			<DBInstanceDescription>gp-bp1408002b6mf7fo9</DBInstanceDescription>
			<InstanceNetworkType>VPC</InstanceNetworkType>
			<VSwitchId>vsw-bp1e55m105fuxg5coy41p</VSwitchId>
			<VpcId>vpc-bp1gvpfymsw2t8cv4o297</VpcId>
			<Engine>gpdb</Engine>
			<ExpireTime>2999-09-08T16:00:00Z</ExpireTime>
			<CreateTime>2018-03-16T07:10:03Z</CreateTime>
			<RegionId>cn-hangzhou</RegionId>
			<EngineVersion>4.3</EngineVersion>
			<LockReason></LockReason>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Postpaid</PayType>
		</DBInstance>
	</Items>
	<PageNumber>1</PageNumber>
	<TotalRecordCount>7</TotalRecordCount>
	<RequestId>BBE00C04-A3E8-4114-881D-0480A72CB92E</RequestId>
	<PageRecordCount>7</PageRecordCount>
</DescribeDBInstancesResponse>
```

**JSON格式**

```
{
    "Items":{
        "DBInstance":[
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"1",
                "DBInstanceId":"gp-bp1gjo105888f3b69",
                "ZoneId":"cn-hangzhou-e",
                "DBInstanceDescription":"gpdb_test",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"vsw-bp13jjr8p2cq6oliv305m",
                "VpcId":"vpc-bp1jjr367nag22y0ywvj6",
                "Engine":"gpdb",
                "ExpireTime":"2019-06-27T16:00:00Z",
                "CreateTime":"2018-06-27T12:07:11Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"1",
                "DBInstanceId":"gp-bp1d2340z5yx6xzhg",
                "ZoneId":"cn-hangzhou-e",
                "DBInstanceDescription":"gp-bp1d2340z5yx6xzhg",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"vsw-bp13jjr8p2cq6oliv305m",
                "VpcId":"vpc-bp1jjr367nag22y0ywvj6",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-06-27T11:51:46Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-bp1lugtm4dn30mg1f",
                "ZoneId":"cn-hangzhou-e",
                "DBInstanceDescription":"测试",
                "InstanceNetworkType":"VPC",
                "VSwitchId":"vsw-bp13jjr8p2cq6oliv305m",
                "VpcId":"vpc-bp1jjr367nag22y0ywvj6",
                "Engine":"gpdb",
                "ExpireTime":"2018-07-27T16:00:00Z",
                "CreateTime":"2018-06-27T11:46:11Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"1",
                "DBInstanceId":"gp-bp16511m0e6km530g",
                "ZoneId":"cn-hangzhou-f",
                "DBInstanceDescription":"测试2",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"",
                "VpcId":"",
                "Engine":"gpdb",
                "ExpireTime":"2018-07-20T16:00:00Z",
                "CreateTime":"2018-06-20T05:42:03Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-bp1xm5o26k5tx08j2",
                "ZoneId":"cn-hangzhou-b",
                "DBInstanceDescription":"gp-bp1xm5o26k5tx08j2",
                "InstanceNetworkType":"VPC",
                "VSwitchId":"vsw-bp1e55m105fuxg5coy41p",
                "VpcId":"vpc-bp1gvpfymsw2t8cv4o297",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-06-05T03:42:41Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-bp1g60zau80mxt9cr",
                "ZoneId":"cn-hangzhou-b",
                "DBInstanceDescription":"测试",
                "InstanceNetworkType":"Classic",
                "VSwitchId":"",
                "VpcId":"",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-05-07T06:48:47Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            },
            {
                "LockMode":"Unlock",
                "DBInstanceNetType":"2",
                "DBInstanceId":"gp-bp1408002b6mf7fo9",
                "ZoneId":"cn-hangzhou-b",
                "DBInstanceDescription":"gp-bp1408002b6mf7fo9",
                "InstanceNetworkType":"VPC",
                "VSwitchId":"vsw-bp1e55m105fuxg5coy41p",
                "VpcId":"vpc-bp1gvpfymsw2t8cv4o297",
                "Engine":"gpdb",
                "ExpireTime":"2999-09-08T16:00:00Z",
                "CreateTime":"2018-03-16T07:10:03Z",
                "RegionId":"cn-hangzhou",
                "EngineVersion":"4.3",
                "LockReason":"",
                "DBInstanceStatus":"Running",
                "PayType":"Postpaid"
            }
        ]
    },
    "PageNumber":1,
    "TotalRecordCount":7,
    "RequestId":"BBE00C04-A3E8-4114-881D-0480A72CB92E",
    "PageRecordCount":7
}

```

