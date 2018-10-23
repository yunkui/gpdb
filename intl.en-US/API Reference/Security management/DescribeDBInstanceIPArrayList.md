# DescribeDBInstanceIPArrayList {#concept_h1y_sgm_q2b .concept}

## Description { .section}

You can call this operation to query the list of whitelists for an instance.

## Request parameters { .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-| Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String| Yes|The operation that you want to perform. Set the value to DescribeDBInstanceIPArrayList.|
|DBInstanceId|String| Yes|The instance name.|

## Response parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_apd_1rv_3bb).|
|Items|List<DBInstanceIPArray\>|The list of whitelists for an instance.|

|Name|Type|Description|
|----|----|-----------|
|DBInstanceIPArrayName|String |The name of the whitelist.|
|DBInstanceIPArrayAttribute|String |This parameter is empty by default. You can use this parameter to specify an attribute for a whitelist. A whitelist with the `hidden` attribute does not appear in the console.|
|SecurityIPList|String |You can add up to 1000 IP addresses to a whitelist. Multiple IP addresses are separated by commas. The format is as follows:-   0.0.0.0/0
-   10.23.12.24 \(IP\)
-   10.23.12.24/24 represents the IPv4 address 10.23.12.24. Its subnet mask is 255.255.255.0, which has 24 leading 1 bits, and its associated routing prefix. The IP address is expressed as Classless Inter-Domain Routing \(CIDR\) notation.

|

## Sample requests { .section}

```
https://gpdb.aliyuncs.com/?Action=DescribeDBInstanceIPArrayList
&DBInstanceId=gp-xxxxxxx
&<Common request parameters>
```

## Sample responses { .section}

**XML format**

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

**JSON format**

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

