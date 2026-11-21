# HTTP protocol

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-basic-http)

#### What is HTTP Protocol?

1. Protocol for browsers (IE, Chrome, Safari, Firefox) to communicate with web servers
2. A simple structure that responds when a request is made from the browser.
3. International order through Internet standards (RFC-2616) established by W3C, IETF, etc.
4. A stable standard used globally for over 20 years, starting with HTTP/0.9 in 1991
5. All software related to WWW follows suit, but some parts must be set by the site administrator according to service characteristics.

![image](https://searchadvisor-phinf.pstatic.net/MjAxOTA5MjFfMjAz/MDAxNTY5MDM0NDU1MTI4.oW2RgBxUCCMOymzbePNv4IAtXooJAOD9vvJE3FJgZpkg.3BIQzX71k2H8u4M7E5yQ924OBk-bWlXujZ62PAWZVb8g.JPEG/http-protocol-1.jpg)

#### HTTP response code

|  | Response code group | response code | explanation |
| --- | --- | --- | --- |
| 1xx | Informational |  |  |
| 2xx | Successful | 200 OK | In the most common case, returning the requested web page |
| 3xx | Redirection | 301 Moved Permanently | The requested URL is completely converted to a URL (specified in the Location: header). The client deletes the requested URL or replaces it with a new URL. |
|  |  | 302 Found | Code left behind to maintain compatibility with HTTP/1.0 and earlier HTTP/1.1. Originally, it indicated that the requested URL had been temporarily changed, unlike 301, but the actual implementation went beyond the intent of the HTTP protocol, so it was enacted separately into 303 and 307. |
|  |  | 303	See Other  | Notifies that the requested URL has been temporarily changed to another URL. The changed URL (designated as Location: header) must be accessed using the GET method. |
|  |  | 307	Temporary Redirect | Notifies that the requested URL has been temporarily changed to another URL. The changed URL (designated as Location: header) must be accessed using the GET method. |
|  |  | 308 Permanent Redirect | The requested URL is completely converted to a URL (specified in the Location: header). Similar to 301 Moved Permanently, but the difference is that the request method (POST, PUT, DELETE, etc.) is maintained.
| 4xx | Client Error | 400 Bad Request | HTTP requests, especially those with incorrect grammar |
|  |  | 401 Unauthorized | If you do not have or lack the required authentication qualifications when accessing a web page |
|  |  | 403 Forbidden | When accessing a web page with authentication information but without permission |
|  |  | 404	Not Found | When accessing a page that does not exist |
| 5xx | Server Error | 500 Internal Server Error | When the web server settings are incorrect or there is an error in the server program. |
|  |  | 503	Service Unavailable | When there are too many requests on the web server or the web server is overloaded and cannot respond. |
