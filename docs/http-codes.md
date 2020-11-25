# HTTP Codes

## HTTP methods

!!! note "GET"
    The resource has been fetched and is transmitted in the message body.

!!! note "HEAD"
    The entity headers are in the message body.

!!! note "PUT or POST"
    The resource describing the result of the action is transmitted in the message body.

!!! note "TRACE"
    The message body contains the request message as received by the server.

`GET`

:   The resource has been fetched and is transmitted in the message body.

`HEAD`

:   The entity headers are in the message body.

`PUT` or `POST`

:   The resource describing the result of the action is transmitted in the message body.

`TRACE`

:   The message body contains the request message as received by the server.

## 2xx

`200 OK`

:   The request has succeeded.

`201 Created`

:   The request has succeeded and a new resource has been created as a result of it.

`202 Accepted`

:   The request has been received but not yet acted upon. It is non-committal, meaning that there is no way in HTTP to later send an asynchronous response indicating the outcome of processing the request. It is intended for cases where another process or server handles the request, or for batch processing.

`203 Non-Authoritative Information`

:   This response code means returned meta-information set is not exact set as available from the origin server, but collected from a local or a third party copy.

`204 No Content`

:   There is no content to send for this request, but the headers may be useful.

`205 Reset Content`

:   This response code is sent after accomplishing request to tell user agent reset document view which sent this request.

`206 Partial Content`

:   This response code is used because of range header sent by the client to separate download into multiple streams.

## 3xx

`300 Multiple Choice`

:   The request has more than one possible response. The user-agent or user should choose one of them. There is no standardized way of choosing one of the responses.

`301 Moved Permanently`

:   This response code means that the URI of the requested resource has been changed permanently.

`302 Found`

:   This response code means that the URI of requested resource has been changed temporarily. New changes in the URI might be made in the future. Therefore, this same URI should be used by the client in future requests.

`303 See Other`

:   The server sent this response to direct the client to get the requested resource at another URI with a GET request.

`304 Not Modified`

:   This is used for caching purposes. It tells the client that the response has not been modified, so the client can continue to use the same cached version of the response.

`307 Temporary Redirect`

:   The server sends this response to direct the client to get the requested resource at another URI with same method that was used in the prior request. This has the same semantics as the `302 Found` HTTP response code, with the exception that the user agent must not change the HTTP method used: If a `POST` was used in the first request, a `POST` must be used in the second request.

`308 Permanent Redirect`

:   This means that the resource is now permanently located at another URI, specified by the `Location:` HTTP Response header. This has the same semantics as the `301 Moved Permanently` HTTP response code, with the exception that the user agent must not change the HTTP method used: If a `POST` was used in the first request, a `POST` must be used in the second request.

## 4xx

`400 Bad Request`

:   This response means that server could not understand the request due to invalid syntax.

`401 Unauthorized`

:   Although the HTTP standard specifies "unauthorized", semantically this response means "unauthenticated". That is, the client must authenticate itself to get the requested response.

`403 Forbidden`

:   The client does not have access rights to the content, i.e. they are unauthorized, so server is rejecting to give proper response. Unlike 401, the client's identity is known to the server.

`404 Not Found`

:   The server can not find requested resource. In the browser, this means the URL is not recognized. In an API, this can also mean that the endpoint is valid but the resource itself does not exist. Servers may also send this response instead of 403 to hide the existence of a resource from an unauthorized client.

`405 Method Not Allowed`

:   The request method is known by the server but has been disabled and cannot be used. For example, an API may forbid DELETE-ing a resource. The two mandatory methods, GET and HEAD, must never be disabled and should not return this error code.

`406 Not Acceptable`

:   This response is sent when the web server, after performing server-driven content negotiation, doesn't find any content following the criteria given by the user agent.

`407 Proxy Authentication Required`

:   This is similar to 401 but authentication is needed to be done by a proxy.

`408 Request Timeout`

:   This response is sent on an idle connection by some servers, even without any previous request by the client. It means that the server would like to shut down this unused connection.

`409 Conflict`

:   This response is sent when a request conflicts with the current state of the server.

`413 Payload Too Large`

:   Request entity is larger than limits defined by server; the server might close the connection or return an `Retry-After` header field.

`418 I'm a teapot`

:   The server refuses the attempt to brew coffee with a teapot.

`429 Too Many Requests`

:   The user has sent too many requests in a given amount of time ("rate limiting").

## 5xx

`500 Internal Server Error`

:   The server has encountered a situation it doesn't know how to handle.

`501 Not Implemented`

:   The request method is not supported by the server and cannot be handled. The only methods that servers are required to support (and therefore that must not return this code) are GET and HEAD.

`502 Bad Gateway`

:   This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.

`503 Service Unavailable`

:   The server is not ready to handle the request. Common causes are a server that is down for maintenance or that is overloaded. Note that together with this response, a user-friendly page explaining the problem should be sent. This responses should be used for temporary conditions and the `Retry-After:` HTTP header should, if possible, contain the estimated time before the recovery of the service. The webmaster must also take care about the caching-related headers that are sent along with this response, as these temporary condition responses should usually not be cached.

`504 Gateway Timeout`

:   This error response is given when the server is acting as a gateway and cannot get a response in time.

`505 HTTP Version Not Supported`

:   The HTTP version used in the request is not supported by the server.

## Thanks

Thanks to the Mozilla foundation for there incredible work. All the info's on this page come from [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
