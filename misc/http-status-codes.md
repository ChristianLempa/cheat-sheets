# HTTP Status Codes
## Categories
-   **1XX** status codes: Informational Requests
-   **2XX** status codes: Successful Requests
-   **3XX** status codes: Redirects
-   **4XX** status codes: Client Errors
-   **5XX** status codes: Server Errors

## Complete List
Code | Name | Description
---|---|---
100|Continue|Everything so far is OK and that the client should continue with the request or ignore it if it is already finished.
101|Switching Protocols|
102|Processing|
103|Early Hints|
200|OK|Successful request
201|Created|The server acknowledged the created resource.
202|Accepted|The client's request has been received but the server is still processing it.
203|Non-Authoritative Information|The response that the server sent to the client is not the same as it was when the server sent it.
204|No Content  
205|Reset Content  
206|Partial Content  
207|Multi-Status  
208|Already Reported  
226|IM Used
300|Multiple Choices  
301|Moved Permanently  
302|Found  
303|See Other  
304|Not Modified  
305|Use Proxy  
307|Temporary Redirect  
308|Permanent Redirect
400|Bad Request  
401|Unauthorized  
402|Payment Required  
403|Forbidden  
404|Not Found  
405|Method Not Allowed  
406|Not Acceptable  
407|Proxy Authentication Required  
408|Request Timeout  
409|Conflict  
410|Gone  
411|Length Required  
412|Precondition Failed  
413|Payload Too Large  
414|Request-URI Too Long  
415|Unsupported Media Type  
416|Requested Range Not Satisfiable  
417|Expectation Failed  
418|I'm a teapot  
421|Misdirected Request  
422|Unprocessable Entity  
423|Locked  
424|Failed Dependency  
426|Upgrade Required  
428|Precondition Required  
429|Too Many Requests  
431|Request Header Fields Too Large  
444|Connection Closed Without Response  
451|Unavailable For Legal Reasons  
499|Client Closed Request
500|Internal Server Error  
501|Not Implemented  
502|Bad Gateway  
503|Service Unavailable  
504|Gateway Timeout  
505|HTTP Version Not Supported  
506|Variant Also Negotiates  
507|Insufficient Storage  
508|Loop Detected  
510|Not Extended  
511|Network Authentication Required  
599|Network Connect Timeout Error