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
101|Switching Protocols|The client has asked the server to change protocols and the server has agreed to do so.
102|Processing|The server has received and is processing the request, but that it does not have a final response yet.
103|Early Hints|Used to return some response headers before final HTTP message.
200|OK|Successful request.
201|Created|The server acknowledged the created resource.
202|Accepted|The client's request has been received but the server is still processing it.
203|Non-Authoritative Information|The response that the server sent to the client is not the same as it was when the server sent it.
204|No Content|There is no content to send for this request
205|Reset Content|Tells the user agent to reset the document which sent this request.
206|Partial Content|This response code is used when the range-header is sent from the client to request only part of a resource.
207|Multi-Status|Conveys information about multiple resources, for situations where multiple status codes might be appropriate.
208|Already Reported|The members of a DAV binding have already been enumerated in a preceding part of the multi-status response.
226|IM Used|IM is a specific extension of the HTTP protocol. The extension allows a HTTP server to send diffs (changes) of resources to clients.
300|Multiple Choices|The request has more than one possible response. The user agent should choose one.
301|Moved Permanently|The URL of the requested resource has been changed permanently. The new URL is given in the response.
302|Found|This response code means that the URI of requested resource has been changed temporarily
303|See Other|The server sent this response to direct the client to get the requested resource at another URI with a GET request.
304|Not Modified|It tells the client that the response has not been modified, so the client can continue to use the same cached version of the response.
305|Use Proxy|Defined in a previous version of the HTTP specification to indicate that a requested response must be accessed by a proxy. (discontinued)
307|Temporary Redirect|The server sends this response to direct the client to get the requested resource at another URI with same method that was used in the prior request.
308|Permanent Redirect|This means that the resource is now permanently located at another URI, specified by the Location: HTTP Response header.
400|Bad Request|The server could not understand the request
401|Unauthorized|The client didn't authenticate himself. 
402|Payment Required|This response code is reserved for future use. The initial aim for creating this code was using it for digital payment systems, however this status code is used very rarely and no standard convention exists.
403|Forbidden|The client does not have access rights to the content
404|Not Found|The server can not find the requested resource
405|Method Not Allowed|The request method is known by the server but is not supported by the target resource
406|Not Acceptable|The reponse doens't conforms to the creteria given by the client
407|Proxy Authentication Required|This is similar to 401 Unauthorized but authentication is needed to be done by a proxy.
408|Request Timeout|This response is sent on an idle connection by some servers, even without any previous request by the client.
409|Conflict|This response is sent when a request conflicts with the current state of the server.
410|Gone|This response is sent when the requested content has been permanently deleted from server, with no forwarding address.
411|Length Required|Server rejected the request because the Content-Length header field is not defined and the server requires it.
412|Precondition Failed|Access to the target resource has been denied.
413|Payload Too Large|Request entity is larger than limits defined by server.
414|Request-URI Too Long|The URI requested by the client is longer than the server is willing to interpret.
415|Unsupported Media Type|The media format is not supported by the server.
416|Requested Range Not Satisfiable|The range specified by the Range header field in the request cannot be fulfilled.
417|Expectation Failed|the expectation indicated by the Expect request header field cannot be met by the server.
418|I'm a teapot|The server refuses the attempt to brew coffee with a teapot.
421|Misdirected Request|The request was directed at a server that is not able to produce a response.
422|Unprocessable Entity|The request was well-formed but was unable to be followed due to semantic errors.
423|Locked|The resource that is being accessed is locked.
424|Failed Dependency|The request failed due to failure of a previous request.
426|Upgrade Required|The server refuses to perform the request using the current protocol but might be willing to do so after the client upgrades to a different protocol.
428|Precondition Required|his response is intended to prevent the 'lost update' problem, where a client GETs a resource's state, modifies it and PUTs it back to the server, when meanwhile a third party has modified the state on the server, leading to a conflict.
429|Too Many Requests|The user has sent too many requests in a given amount of time
431|Request Header Fields Too Large|The server is can't process the request because its header fields are too large.
444|Connection Closed Without Response|The connection opened, but no data was written.
451|Unavailable For Legal Reasons|The user agent requested a resource that cannot legally be provided (such as a web page censored by a government)
499|Client Closed Request|The client closed the connection, despite the server was processing the request already.
500|Internal Server Error|The server has encountered a situation it does not know how to handle.
501|Not Implemented|The request method is not supported by the server and cannot be handled.
502|Bad Gateway|This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.
503|Service Unavailable|The server is not ready to handle the request.
504|Gateway Timeout|This error response is given when the server is acting as a gateway and cannot get a response in time.
505|HTTP Version Not Supported|The HTTP version used in the request is not supported by the server.
506|Variant Also Negotiates|the chosen variant resource is configured to engage in transparent content negotiation itself, and is therefore not a proper end point in the negotiation process.
507|Insufficient Storage|The method could not be performed on the resource because the server is unable to store the representation needed to successfully complete the request.
508|Loop Detected|The server detected an infinite loop while processing the request.
510|Not Extended|Further extensions to the request are required for the server to fulfill it.
511|Network Authentication Required|Indicates that the client needs to authenticate to gain network access.
599|Network Connect Timeout Error|The connection timed out due to a overloaded server, a hardware error or a infrastructure error.
