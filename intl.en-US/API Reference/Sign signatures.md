# Sign signatures {#reference_xmy_kxl_q2b .reference}

The HybridDB for PostgreSQL service performs identity authentication on each access request. Therefore, whether submitted through HTTP or HTTPS, a request must contain signature information. HybridDB for PostgreSQL uses symmetric encryption based on an Access Key ID and Access Key Secret to verify the identity of request senders. The Access Key ID and Access Key Secret are issued to users by Alibaba Cloud \(users can request and manage keys on the website of Alibaba Cloud\). The Access Key ID indicates the identity of the user. The Access Key Secret is the secret key used to encrypt the signature string and to verify the signature string on the server. It must be kept strictly confidential and only be known to Alibaba Cloud and authenticated users.

Follow the instructions below to sign the signatures for your requests.

1.  Use request parameters to construct a Canonicalized Query String.
    1.  Sort all request parameters \(including "Common request parameters" and user-defined parameters for the given request interfaces described in this document, excluding the Signature parameter mentioned in "Common request parameters"\) alphabetically by the parameter name.

        **Note:** If you use the GET method to submit requests, these parameters are included in the request URI that is the part after the question mark “?” following the ampersand “&” in the URI.

    2.  Encode the name and value of each request parameter. The names and values must undergo URL encoding using the UTF-8 character set. The URL encoding rules are as follows:

        -   Uppercase letters \(A–Z\), lowercase letters \(a–z\), numbers \(0–9\), hyphens \(-\), underscores \(\_\), periods \(.\), and tildes \(~\) are not encoded.
        -   Other characters are encoded in "%XY" format, with XY representing the character ASCII code in hexadecimal notation. The double quotation mark \("\) is coded as %22.
        -   Extended UTF-8 characters are encoded in “%XY%ZA… ”
        -   It must be noted that an English space is encoded as %20, rather than the plus sign \(+\).
        **Note:** Generally, URL encoding libraries \(such as “java.net.URLEncoder” in Java\) perform encoding based on rules of the MIME type in the “application/x-www-form-urlencoded” format. You can use this encoding method directly by replacing the plus sign \(+\) in the encoded string with "%20", the asterisk \(\*\) with "%2A", and change "%7E" back to the tilde \(~\) to conform to the encoding rules described above .

    3.  Connect the encoded parameter names and values with equal signs \(=\).
    4.  Then, sort the parameter name and value pairs connected by equal signs in alphabetical order, and connect them with an ampersand \(&\) to produce the canonicalized query string.
2.  Follow the rules below to use the canonicalized query string to construct the string for signature calculation:

    ```
    StringToSign= HTTPMethod + “&" + percentEncode(“/") + "&" + 
    percentEncode(CanonicalizedQueryString) 
    
    ```

    In this formulation, HTTPMethod is the HTTP method \(such as GET\) used for request submission.

    percentEncode\(“/“\): the coded value for the character “/“ according to the URL encoding rules described in 1.b, namely, “%2F”.

    “percentEncode\(“/“\)” is the encoded value \(namely, “%2F”\) for the character “/“ according to the URL encoding rules described in 1.b.

3.  Use the string for signature calculation to calculate the HMAC value of the signature based on [RFC2104](http://www.ietf.org/rfc/rfc2104.txt).

    **Note:** Note: The key used for calculating the signature is the AccessKey NOTE: The key used for signature calculation is your secret access key adding the ampersand “&” \(ASCII:38\) and it is based on the SHA1 hashing algorithm.

4.  Encode the HMAC value into a string based on Base64 encoding rules to obtain the signature value.
5.  Add the obtained signature value to request parameters as the Signature parameter to complete the request signing process.

    **Note:** 

    NOTE: The obtained signature value requires URL encoding based on the [RFC3986](http://tools.ietf.org/html/rfc3986) rule like other parameters before it is submitted to the GPDB server as the final request parameter value. Take "DescribeDBInstances" as an example, the request URL before a signature is:

    ```
    http://gpdb.aliyuncs.com/?Timestamp=2013-06-01T10:33:56Z&Format=XML&Acce ssKeyId=testid&Action=DescribeDBInstances&SignatureMethod=HMAC-SHA1&Regi onId=region1&SignatureNonce=NwDAxvLU6tFE0DVb&Version=2014-08-15&Signatur eVersion=1.0
    ```

    The corresponding "StringToSign" is:

    ```
    GET&%2F&AccessKeyId%3Dtestid%26Action%DescribeDBInstances%26Format%3DXML %26RegionId%3Dregion1%26SignatureMethod%3DHMAC-SHA1%26SignatureNonce%3DN wDAxvLU6tFE0DVb%26SignatureVersion%3D1.0%26Timestamp%3D2013-06-01T10%253 A33%253A56Z%26Version%3D2014-08-15 
    ```

    Assume that the value of the Access Key ID parameter value is "testid," the value of the Access Key Secret parameter is "testsecret." Then the key used for HMAC calculation is "testsecret&," and the calculated signature value is :

    GfQRtWbwdE8sp7q9lBgZyutVht8=

    The signed request URL is \(with the Signature parameter added\):

    ```
    http://gpdb.aliyuncs.com/?Timestamp=2012-12-26T10%3A33%3A56Z&Format=XML& AccessKeyId=testid&Action=DescribeDBInstances&SignatureMethod=HMAC-SHA1& RegionId=region1&SignatureNonce=NwDAxvLU6tFE0DVb&Version=2012-09-13&Sign atureVersion=1.0&Signature= GfQRtWbwdE8sp7q9lBgZyutVht8%3d
    ```


