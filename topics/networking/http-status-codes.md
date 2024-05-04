# [Every HTTP Response Status Code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

- Informational Responses (100–199)
- Successful Responses (200–299)
- Redirection Messages (300–399)
- Client Error Responses (400–499)
- Server Error Responses (500–599)

## 1×× Informational HTTP status codes

**100 Continue**
- Purpose: Allows the client to continue sending the remainder of the request. Useful when the request has a large body, and the client wants to ensure the server is willing to process the request before sending the entire body.
- Example: A client sends an HTTP request with a header including Expect: 100-continue and waits for the server to respond with 100 Continue before sending the body of the request.

**101 Switching Protocols**
- Purpose: Used by the server to indicate that it agrees to switch protocols as requested by a client.
- Example: A client sends an HTTP upgrade request to begin communicating over WebSocket instead of HTTP. The server agrees and responds with 101 Switching Protocols, then begins communicating over the new protocol.

**102 Processing**
- Purpose: Indicates that the server has received and is processing the request, but no response is available yet. This prevents the client from timing out and assuming the request was lost.
- Example: A client submits a request that requires extensive processing (like a complex database query). The server responds with 102 Processing to let the client know it is still actively processing the request but needs more time to complete it.

**103 Early Hints**
- Purpose: Used to return some response headers before final HTTP message. The intent is to allow a client to start preloading resources while the server is still preparing a response.
- Example: Before sending a full response for a web page, the server sends 103 Early Hints with Link headers for stylesheets and scripts the client will need. This allows the client to fetch these resources while waiting for the full HTTP response.

## 2×× Success codes HTTP status codes

**200 OK**
- Purpose: The request has succeeded, and the response contains the requested data.
- Example: A client sends a GET request for a webpage, and the server responds with 200 OK along with the HTML content of the page.

**201 Created**
- Purpose: The request has succeeded and resulted in the creation of a new resource.
- Example: A client sends a POST request to create a new user account, and the server responds with 201 Created along with a location header pointing to the new resource.

**202 Accepted**
- Purpose: The request has been accepted for processing, but the processing has not been completed.
- Example: A client submits a request to start a batch job that takes a long time to process. The server responds with 202 Accepted to acknowledge the request.

**203 Non-authoritative Information**
- Purpose: The server is a transforming proxy that received a 200 OK from its origin, but is returning a modified version of the origin's response.
- Example: A client requests data from a server, which retrieves data from another source and modifies it before sending it back with 203 Non-authoritative Information.

**204 No Content**
- Purpose: The server successfully processed the request, but is not returning any content.
- Example: A client sends a DELETE request to remove a resource. The server successfully deletes the resource and responds with 204 No Content.

**205 Reset Content**
- Purpose: The server successfully processed the request and is instructing the client to reset its document view.
- Example: A form submission is processed, and the server responds with 205 Reset Content to clear the form fields.

**206 Partial Content**
- Purpose: The server is delivering only part of the resource due to a range header sent by the client.
- Example: A client requests a range of bytes from a large file, and the server responds with 206 Partial Content containing that segment.

**207 Multi-Status**
- Purpose: Conveys information about multiple resources, typically used for WebDAV operations.
- Example: A client requests multiple operations on different resources (like a batch update), and the server responds with 207 Multi-Status detailing the outcome for each.

**208 Already Reported**
- Purpose: Used inside a DAV: propstat response element to avoid repeatedly enumerating the internal members of multiple bindings to the same collection.
- Example: In a WebDAV request, a subpart of the resource has been reported earlier in the multistatus response, and 208 Already Reported prevents redundancy.

**226 IM Used**
- Purpose: The server has fulfilled a GET request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance.
- Example: A client requests a version of a page that includes inline information derived from multiple sources. The server applies instance manipulations (like content negotiation) and responds with 226 IM Used showing the combined view.

## 3×× Redirection HTTP status codes

**300 Multiple Choices**
- Purpose: Indicates multiple options for the resource that the client may follow, usually for different formats of a resource or different video resolutions.
- Example: A client requests a video, and the server responds with 300 Multiple Choices to offer different video quality levels or file formats.

**301 Moved Permanently**
- Purpose: The requested resource has been assigned a new permanent URI, and any future references should use one of the returned URIs.
- Example: A client requests an old URL, and the server responds with 301 Moved Permanently and a Location header to direct the client to the new URL permanently.

**302 Found (Previously "Moved Temporarily"):**
- Purpose: Tells the client that the resource is temporarily located at another URI, and the client should use it for future requests.
- Example: A client accesses a temporary campaign page, and the server responds with 302 Found redirecting to this temporary address.

**303 See Other:**
- Purpose: The response to the request can be found under another URI using the GET method and should be retrieved using a GET request.
- Example: After a POST operation that submits form data, the server responds with 303 See Other and a Location header pointing to a confirmation or thank you page.

**304 Not Modified:**
- Purpose: Indicates that the resource has not been modified since the last request where the client provided an ETag or last-modified date, which allows the client to continue using a cached version of the resource.
- Example: A client sends a conditional GET request with an If-None-Match or If-Modified-Since header, and the server responds with 304 Not Modified as the resource hasn’t changed.

**305 Use Proxy:**
- Purpose: Indicates that the requested resource must be accessed through the proxy given by the Location field. This status code is no longer recommended due to security concerns.
- Example: A client requests a resource, and the server responds with 305 Use Proxy directing the client to use a specific proxy to access the information.

**307 Temporary Redirect:**
- Purpose: Indicates that the requested resource is temporarily under a different URI, similar to 302 but with the guarantee that the method and the body will not be changed when the requested resource is redirected.
- Example: A client requests a document during site maintenance, and the server responds with 307 Temporary Redirect to a maintenance page.

**308 Permanent Redirect:**
- Purpose: The resource is permanently moved to a new location, and all future requests should use one of the returned URIs. Similar to 301 but with the guarantee that the method and body will not be changed.
- Example: A client requests an old URL, and the server responds with 308 Permanent Redirect, ensuring that all future submissions (like POSTs) are redirected to the new URL permanently.

## 4×× Client Error HTTP status codes

**400 Bad Request**
- Purpose: The request cannot be processed due to bad syntax, excessive size, or another client error.
- Example: A client sends a request with malformed syntax, and the server responds with 400 Bad Request.

**401 Unauthorized**
- Purpose: The request lacks valid authentication credentials for the target resource.
- Example: A client tries to access a protected resource without providing authentication credentials and receives 401 Unauthorized.

**402 Payment Required**
- Purpose: Reserved for future use, potentially for digital payment systems.
- Example: Currently, this status is largely unused but could be employed to require payment before accessing a resource.

**403 Forbidden**
- Purpose: The server understood the request but refuses to authorize it.
- Example: A client tries to access forbidden directory listings on a server and receives 403 Forbidden.

**404 Not Found**
- Purpose: The server can't find the requested resource.
- Example: A client requests a page that doesn't exist, and the server responds with 404 Not Found.

**405 Method Not Allowed**
- Purpose: The request method is known by the server but has been disabled and cannot be used.
- Example: A client attempts to use PUT where it is not supported and receives 405 Method Not Allowed.

**406 Not Acceptable**
- Purpose: The server cannot produce a response matching the list of acceptable values defined in the request's proactive content negotiation headers.
- Example: A client requests a format via Accept headers that the server cannot provide, resulting in 406 Not Acceptable.

**407 Proxy Authentication Required**
- Purpose: Similar to 401, but authentication must be performed by a proxy.
- Example: A client request must authenticate with a proxy to proceed, resulting in 407 Proxy Authentication Required.

**408 Request Timeout**
- Purpose: The server timed out waiting for the request.
- Example: A client takes too long to send the request, leading the server to respond with 408 Request Timeout.

**409 Conflict**
- Purpose: The request conflicts with the current state of the server.
- Example: A client tries to put the server's resource into an inconsistent state, receiving 409 Conflict.

**410 Gone**
- Purpose: The resource requested is no longer available and will not be available again.
- Example: A client requests a deleted resource, and the server responds with 410 Gone.

**411 Length Required**
- Purpose: The server rejects the request because the Content-Length header is not defined.
- Example: A client sends a POST request without a Content-Length header, resulting in 411 Length Required.

**412 Precondition Failed**
- Purpose: One or more conditions in the request header fields evaluated to false when tested on the server.
- Example: A client sends headers like If-Match with a version that doesn't match the current resource version, causing 412 Precondition Failed.

**413 Payload Too Large**
- Purpose: The server is refusing to process a request because the request payload is larger than the server is willing or able to process.
- Example: A client tries to upload a file that exceeds the server's limit, resulting in 413 Payload Too Large.

**414 Request-URI Too Long**
- Purpose: The URI requested by the client is longer than the server is willing to interpret.
- Example: A client sends a GET request with an excessively long URL, leading to 414 Request-URI Too Long.

**415 Unsupported Media Type**
- Purpose: The media format of the requested data is not supported by the server, so the server is rejecting the request.
- Example: A client posts JSON data but the server only supports form data, resulting in 415 Unsupported Media Type.

**416 Requested Range Not Satisfiable**
- Purpose: The client has asked for a portion of the file, but the server cannot supply that portion.
- Example: A client requests a range of bytes in a file that is beyond the file's size, causing 416 Requested Range Not Satisfiable.

**417 Expectation Failed**
- Purpose: The server cannot meet the requirements of the Expect request-header field.
- Example: A client includes an Expect header that the server cannot meet, resulting in 417 Expectation Failed.

**418 I'm a teapot (April Fools' joke)**
- Purpose: A server refuses the attempt to brew coffee with a teapot.
- Example: A client sends a request to a teapot to brew coffee, receiving 418 I'm a teapot.

**421 Misdirected Request**
- Purpose: The request was directed at a server that is not able to produce a response.
- Example: A request is sent to a server that is not configured to produce responses for the combination of scheme and authority included in the request URI.

**422 Unprocessable Entity**
- Purpose: The request was well-formed but was unable to be followed due to semantic errors.
- Example: A client submits an XML request but the XML is unprocessable due to logical errors, resulting in 422 Unprocessable Entity.

**423 Locked**
- Purpose: The resource being accessed is locked.
- Example: A client attempts to modify a resource that is locked by another process, receiving 423 Locked.

**424 Failed Dependency**
- Purpose: The request failed due to the failure of a previous request.
- Example: A request depends on another request which failed, leading to 424 Failed Dependency.

**426 Upgrade Required**
- Purpose: The client should switch to a different protocol such as TLS/1.0.
- Example: A client is told by the server that it must upgrade to a newer protocol, receiving 426 Upgrade Required.

**428 Precondition Required**
- Purpose: The server requires the request to be conditional.
- Example: To prevent the 'lost update' problem, conditions like If-Match must be used, leading to 428 Precondition Required.

**429 Too Many Requests**
- Purpose: The user has sent too many requests in a given amount of time ("rate limiting").
- Example: A client has been rate-limited after sending too many requests too quickly, resulting in 429 Too Many Requests.

**431 Request Header Fields Too Large**
- Purpose: The server is unwilling to process the request because its header fields are too large.
- Example: A client sends a request with header fields too large for the server to process, causing 431 Request Header Fields Too Large.

**444 Connection Closed Without Response**
- Purpose: A non-standard status code used to indicate that the server returned no information to the client and closed the connection.
- Example: Often used by servers like Nginx when they perform a hard denial of a request without explaining why.

**451 Unavailable For Legal Reasons**
- Purpose: The server is denying access to the resource as a consequence of a legal demand.
- Example: A client requests content that has been legally blocked, resulting in 451 Unavailable For Legal Reasons.

**499 Client Closed Request**
- Purpose: A non-standard status code introduced by Nginx for the case when a client closes the connection while the server is still processing its request.
- Example: The client disconnects or the browser stops the request before the server finished retrieving data, leading to 499 Client Closed Request.

## 5×× Server Error HTTP status codes

**500 Internal Server Error**
- Purpose: A generic error message when the server encounters an unexpected condition.
- Example: A client sends a request, but the server has a misconfiguration or a runtime error occurs, leading to a 500 Internal Server Error.

**501 Not Implemented**
- Purpose: The server either does not recognize the request method, or it lacks the ability to fulfill the request.
- Example: A client sends a request using a HTTP method that the server does not support, resulting in 501 Not Implemented.

**502 Bad Gateway**
- Purpose: The server, while acting as a gateway or proxy, received an invalid response from the upstream server.
- Example: A proxy server attempts to communicate with an upstream server, but gets an invalid or no response, leading to 502 Bad Gateway.

**503 Service Unavailable**
- Purpose: The server is currently unavailable (due to overload or maintenance).
- Example: A client accesses a website, but the server is temporarily down for maintenance, resulting in 503 Service Unavailable.

**504 Gateway Timeout**
- Purpose: The server, while acting as a gateway or proxy, did not receive a timely response from the upstream server.
- Example: A proxy server did not receive a response from an upstream server within the timeout period, leading to 504 Gateway Timeout.

**505 HTTP Version Not Supported**
- Purpose: The server does not support the HTTP protocol version used in the request.
- Example: A client sends a request using HTTP/3.0 which the server does not support, resulting in 505 HTTP Version Not Supported.

**506 Variant Also Negotiates**
- Purpose: Transparent content negotiation for the request results in a circular reference.
- Example: A server error in content negotiation where the chosen variant is configured to engage in further negotiation, causing 506 Variant Also Negotiates.

**507 Insufficient Storage**
- Purpose: The server is unable to store the representation needed to complete the request.
- Example: A WebDAV request requires storage of a large resource, but the server has insufficient space, leading to 507 Insufficient Storage.

**508 Loop Detected**
- Purpose: The server detected an infinite loop while processing the request.
- Example: In a WebDAV setup, a recursive link causes the server to loop indefinitely, resulting in 508 Loop Detected.

**510 Not Extended**
- Purpose: Further extensions to the request are required for the server to fulfill it.
- Example: A client request lacks necessary extensions that a server requires before processing, leading to 510 Not Extended.

**511 Network Authentication Required**
- Purpose: The client needs to authenticate to gain network access.
- Example: Intercepting proxies used in networks (like WiFi hotspots) requiring authentication before granting Internet access, leading to 511 Network Authentication Required.

**599 Network Connect Timeout Error**
- Purpose: This non-standard status code indicates that the connection timed out when the client attempted to communicate with the server.
- Example: A client's attempt to connect to the server times out due to network issues, leading to 599 Network Connect Timeout Error.