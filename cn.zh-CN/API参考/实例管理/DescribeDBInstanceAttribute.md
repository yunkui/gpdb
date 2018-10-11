# DescribeDBInstanceAttribute {#concept_isw_gbm_q2b .concept}

## 描述 { .section}

查询实例详情。

## 输入参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值：DescribeDBInstanceAttribute。|
|DBInstanceId|String|是|实例名。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详情请参见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_apd_1rv_3bb)。|
|Items|List<DBInstanceAttribute\>|实例详情列表。|

|名称|类型|描述|
|--|--|--|
|AvailabilityValue|String|查询当前实例可用性状态，单位：百分比。|
|ConnectionMode|String| -   Performance：标准访问模式。
-   Safty：高安全访问模式。

 |
|ConnectionString|String|连接地址。|
|CreationTime|String|创建时间，格式：`YYYY-MM-DDThh:mm:ssZ`，如2011-05-30T12:11:4Z。|
|DBInstanceClass|String|实例规格。|
|DBInstanceClassType|String|实例规格族：-   s：共享型
-   x：通用型
-   d：独享套餐
-   h：独占物理机

|
|DBInstanceCpuCores|String|CPU核数。|
|DBInstanceDescription|String|实例描述。|
|DBInstanceDiskMBPS|Long|Group最大的BPS（磁盘吞吐量），单位:Mbps。|
|DBInstanceGroupCount|String|计算组Group数量。|
|DBInstanceId|String|实例名。|
|DBInstanceMemory|Long|实例内存，单位：MB。|
|DBInstanceNetType|String| -   Internet：外网 。
-   Intranet：内网。

 |
|DBInstanceStatus|String|实例状态，详见[实例状态表](intl.zh-CN/API参考/附录/实例状态表.md#)。|
|DBInstanceStorage|Long|实例存储空间，单位：GB。|
|Engine|String| -   Internet：外网。
-   Intranet：内网。

 |
|EngineVersion|String|数据库版本。|
|ExpireTime|String|过期时间。|
|HostType|String|计算组机器类型取值：-   0：SSD
-   1：SATA

。|
|InstanceNetworkType|String| -   Classic：经典网络。
-   VPC：VPC网络。

 |
|LockMode|String| -   Unlock：正常 。
-   ManualLock：手动触发锁定 。
-   LockByExpiration：实例过期自动锁定 。
-   LockByRestoration：实例回滚前的自动锁定 。
-   LockByDiskQuota：实例空间满自动锁定。

 |
|MaintainEndTime|String|可维护截止时间。|
|MaintainStartTime|String|可维护开始时间。|
|MaxConnections|Integer|最大实例并发连接数。|
|PayType|String|计费类型：-   Postpaid：按量付费。
-   Prepaid：包年包月。

|
|Port|String|应用访问端口。|
|RegionId|String|地域。|
|SecurityIPList|String|允许访问的IP名单。|
|VpcId|String|开启ClassicLink的VPC ID。|
|ZoneId|String|可用区。|

## 请求示例 { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstanceAttribute
&DBInstanceId=gp-xxxxxxx
&<公共请求参数>

```

**返回示例**

**XML格式**

```
<DescribeDBInstanceAttributeResponse>
  <RequestId>B4CAF581-2AC7-41AD-8940-D56DF7AADF5B</RequestId>
  <Items>
    <DBInstanceAttribute>
			<DBInstanceDiskMBPS>300</DBInstanceDiskMBPS>
			<ConnectionString>gp-xxxxxxx.gpdb.rds.aliyuncs.com</ConnectionString>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<ConnectionMode>Performance</ConnectionMode>
			<VpcId>vpc-xxxxxxxx</VpcId>
			<Engine>gpdb</Engine>
			<MaxConnections>500</MaxConnections>
			<MaintainStartTime>18:00Z</MaintainStartTime>
			<DBInstanceGroupCount>2</DBInstanceGroupCount>
			<HostType>0</HostType>
			<DBInstanceMemory>16384</DBInstanceMemory>
			<EngineVersion>4.3</EngineVersion>
			<DBInstanceStatus>Running</DBInstanceStatus>
			<PayType>Prepaid</PayType>
			<LockMode>Unlock</LockMode>
			<DBInstanceNetType>1</DBInstanceNetType>
			<MaintainEndTime>22:00Z</MaintainEndTime>
			<DBInstanceClass>gpdb.group.segsdx2</DBInstanceClass>
			<DBInstanceId>gp-xxxxxxx</DBInstanceId>
			<DBInstanceClassType>x</DBInstanceClassType>
			<InstanceNetworkType>Classic</InstanceNetworkType>
			<DBInstanceDescription>gp-xxxxxxx/DBInstanceDescription>
			<DBInstanceStorage>160</DBInstanceStorage>
			<CreationTime>2018-06-27T12:07:10Z</CreationTime>
			<Port>3432</Port>
			<ExpireTime>2019-06-27T16:00:00Z</ExpireTime>
			<RegionId>cn-hangzhou</RegionId>
			<AvailabilityValue>100.0%</AvailabilityValue>
			<DBInstanceCpuCores>2</DBInstanceCpuCores>
			<SecurityIPList>127.0.0.1</SecurityIPList>
    </DBInstanceAttribute>
  </Items>
</DescribeDBInstanceAttributeResponse>
```

**JSON格式**

```
{
    "Items":{
        "DBInstanceAttribute":[
            {
                "DBInstanceDiskMBPS":300,
                "ConnectionString":"gp-xxxxxxx.gpdb.rds.aliyuncs.com",
                "ZoneId":"cn-hangzhou-e",
                "ConnectionMode":"Performance",
                "VpcId":"vpc-xxxxxxxx",
                "Engine":"gpdb",
                "MaxConnections":500,
                "MaintainStartTime":"18:00Z",
                "DBInstanceGroupCount":"2",
                "HostType":"0",
                "DBInstanceMemory":16384,
                "EngineVersion":"4.3",
                "DBInstanceStatus":"Running",
                "PayType":"Prepaid",
                "LockMode":"Unlock",
                "DBInstanceNetType":"1",
                "MaintainEndTime":"22:00Z",
                "DBInstanceClass":"gpdb.group.segsdx2",
                "DBInstanceId":"gp-xxxxxxx",
                "DBInstanceClassType":"x",
                "InstanceNetworkType":"Classic",
                "DBInstanceDescription":"gp-xxxxxxx",
                "DBInstanceStorage":160,
                "CreationTime":"2018-06-27T12:07:10Z",
                "Port":"3432",
                "ExpireTime":"2019-06-27T16:00:00Z",
                "RegionId":"cn-hangzhou",
                "AvailabilityValue":"100.0%",
                "DBInstanceCpuCores":2,
                "SecurityIPList":"127.0.0.1"
            }
        ]
    },
    "RequestId":"B4CAF581-2AC7-41AD-8940-D56DF7AADF5B"
}
```

