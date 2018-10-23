# Responses {#reference_emh_dmm_q2b .reference}

After the API is called, the data is returned in the same format. A returned HTTP status code of 2xx indicates that the call has been successful. A returned HTTP status code of 4xx indicates that the call has failed.

Successful responses are returned in XML or JSON format. You can pass a parameter to specify the response format when you call the API from an external system. The default format is XML. The examples of returned results in this topic are formatted for ease of reading. The actual returned results are not formatted with line breaks, indentation, or other layouts.

## Successful response examples {#section_yhf_1rv_3bb .section}

**XML format**

The XML response contains information on whether the request is successful and the specific service data. The example is as follows.

```
<? xml version="1.0" encoding="utf-8"? >  
<!—Result root node--> 
<API name+Response> 
    <!—Returned request tag--> 
 <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId> 
    <!—Returned results--> 
</API name+Response>

```

**JSON format**

```
{ 
    "RequestId": "4C467B38-3910-447D-87BC-AC049166F216", 
    /* Returned results*/ 
} 

```

## Error response examples {#section_xcw_t1x_3bb .section}

If the API call fails, no data is returned. To identify the cause of an error, you can see the appendix [Error Codes](reseller.en-US/API Reference/Error Codes.md#).

When the call fails, an HTTP status code of 4xx or 5xx is returned. The response body contains the error code and the error message. It also contains the GUID "RequestId" and the requested "HostId." If you cannot find the cause of the error, contact Alibaba Cloud Customer Service and provide the HostId and RequestId, so that we can solve your problem as soon as possible.

**XML format**

```
<? xml version="1.0" encoding="UTF-8"? > 
<Error> 
   <RequestId>8906582E-6722-409A-A6C4-0E7863B733A5</RequestId> 
   <HostId>gpdb.aliyuncs.com</HostId> 
   <Code>InvalidAction</Code> 
   <Message>The specified action is not supported. </Message> 
</Error> 

```

**JSON format**

```
{ 
    "RequestId": "7463B73D-35CC-4D19-A010-6B8D65D242EF", 
    "HostId": "gpdb.aliyuncs.com", 
    "Code": "InvalidAction", 
    "Message": "The specified action is not valid." 
} 

```

