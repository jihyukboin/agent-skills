# Requesting page updates

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/indexnow-request)

### Request an update for one page

Use HTTP requests to notify search engines that a page on your website has been updated.

#### request format
```
GET https://searchadvisor.naver.com/indexnow
 ?url=문자열
 &key=문자열
 &[keyLocation=문자열]
```

* url (required): Specify the url you want to notify search engines of updates.  It must be a URL string that conforms to the [RFC3986](https://www.ietf.org/rfc/rfc3986.txt) standard.
* key (required): A key string that proves that you are the owner of the website.
* keyLocation (optional): The key file location is located at the root of the website by default, but can be specified anywhere if necessary.

For key and keyLocation, please also refer to the [link](generating-an-api-key.md) document.

###  Request updates for multiple pages
It uses Json data in an HTTP POST request to notify search engines that the website page has been updated.
You can notify updates to multiple URLs at once.

#### Request format
```
POST /indexnow HTTP/1.1
Content-Type: application/json; charset=utf-8
Host: searchadvisor.naver.com
{
    "host": "www.example.com",
    "key": "0f26d5e892544f74b806ec5c5522e6a1",
    "keyLocation": "https://www.example.com/myIndexNowKey63638.txt",
    "urlList": [
        "https://www.example.com/url1",
        "https://www.example.com/folder/url2",
        "https://www.example.com/url3"
    ]
}
```

* host: Enter the website domain.
* key: A key string that proves that you are the owner of the website.
* keyLocation (optional): The key file location is located at the root of the website by default, but can be specified anywhere if necessary.
* urlList: Specify the urls you want to notify search engines that they have been updated.  It must be a URL string that conforms to the [RFC3986](https://www.ietf.org/rfc/rfc3986.txt) standard. A single POST request can contain up to 10,000 URLs.

For key and keyLocation, please also refer to the [link](generating-an-api-key.md) document.

### HTTP response format from API
HTTP Code  | response message | explanation
----|-----|------
200 | Success	| Transmission was successful. |
202 | Accepted | URL information has been received. Checking key information.  |
400|  Bad request  | The request was made in an incorrect format. |
403|  Forbidden | key is invalid. |
422|  Unprocessable Entity | The URL does not match the key information.  |
429|  Too Many Requests | You are sending too many requests.  |
500|  Server error | Server error. |
