# Crawl request API specification and integration

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/crawl-request-api)

### Precautions before using API
#### Please apply for a partnership proposal.
Please apply by writing [Naver partnership proposal](https://www.navercorp.com/naver/proposalRegister). After applying for a partnership proposal, detailed discussions can be held through the person in charge.
* Affiliate site desired: Naver
* Affiliation category: Website-Collection Request API

![image](https://searchadvisor-phinf.pstatic.net/MjAyMzAzMjlfNTQg/MDAxNjgwMDc2MzQzMzU5.dOM8YOAYov-OtvNEfT2M-qitM3ubC4b6XLP7JJnqQq4g.9SmP73WFI1HBsSKbD6H6wcm0zzn1bYpxmnq2lf2kx2kg.PNG/request_crawl_form.png)

#### Please verify ownership of the site first.
In order to use the crawl request API, site ownership must first be verified in Webmaster Tools.  Please refer to the [Confirmation of ownership](../faq/site-registration-and-ownership-verification.md) FAQ to verify site ownership. When using the crawl request API, if a request is made for a site whose ownership is not confirmed, it will be treated as an error. Additionally, when verifying site ownership, if the url scheme, presence of www, port, etc. are different, it is recognized as a separate site, so the site whose ownership is confirmed and the site specified in the crawl request API must exactly match.

#### Please check robots.txt.
URLs to be collected through the crawl request API must be able to be collected by the Naver crawler.  Please refer to the [Setting up robots.txt](../seo-basics/configuring-robots-txt.md) guide to check whether collection of the target URL is allowed.

#### Please check the accessToken for authentication.
For affiliated users, if you look at the tool settings screen provided by Search Advisor's Webmaster Tools, API affiliation status and API accessToken are displayed.
![image](https://searchadvisor-phinf.pstatic.net/MjAyMDA5MTRfMjkz/MDAxNjAwMDYwODA0ODI3.rfK1ueiY3joqxbwXeUXPjsTl6Rd1p3zWsR3THSjhIssg._FU_vZYnAmF-fY-nhP6JiYgLtko18GmGDM9bETjWewAg.PNG/tool-config.png)
When calling any API, please enter the corresponding accessToken in Bearer form in the Authorization field of the http header. (Example: Authorization: Bearer AAAAO...[ACCESS TOKEN information]...) The example below is an example using the curl command provided in a Linux environment.
```
// 아래 accessToken 영역에 서치어드바이저에서 발급받은 토큰 정보를 넣어주세요.(예: Authorization: Bearer AAAAO...[ACCESS TOKEN 정보]...)
$ curl -v -H "Authorization: Bearer accessToken" -H "Content-Type: application/json" ...
```

#### Please request the URL for crawl request as the URL of the landing page.
Please request collection only from landing pages that general users can view in their browsers.
If the URL displayed in the browser is different from the request URL or the request URL is redirected, collection delays or collection failures may occur. In this case, it is categorized as ‘update failure’ and counted.
```
좋은 요청 예)
  수집 요청 URL : http://www.your-site.com/1
  수집 완료 URL : http://www.your-site.com/1

나쁜 요청 예)
  수집 요청 URL : http://www.your-site.com/1 -> http://www.redirect-site.com/1 (302 Redirect)
  수집 완료 URL : http://www.redirect-site.com/1
```

#### Please request via representative URL.
If the URL is different but the document content is the same, please select a representative URL and request only one.
If multiple URLs are requested, duplicate documents may be collected and URLs that the user does not want may be selected as representatives.
If multiple URLs exist, add canonical meta as the representative URL or redirect to the representative URL.
Alternatively, we suggest requesting only one URL through URL cleanup.
Note:[guide](../seo-basics/building-a-website.md)
```
대표 URL 선정 예)
1. http://www.your-site.com/dir?id=1
2. http://www.your-site.com/dir?id=1&type=
3. http://www.your-site.com/dir?id=1&type=&sort=
4. http://www.your-site.com/dir?id=1&type=&sort=&key=1

1 ~ 4번 URL이 모두 동일 문서라면, 불필요한 query가 정리된 1번 URL을 대표로 선정하여 요청한다.
```


#### URL endpoint
The crawl request API provides the following two types.
* url submit
  * This is an API that submits a list of URLs for collection requests and deletion, and the call URL is as follows.
  * `https://apis.naver.com/searchadvisor/crawl-request/submit.json`
* url verify
  * This is an API that checks if there are any problems with the grammar of the URL list for collection requests and deletion. It is provided for verification of the request body (payload) used when calling url submit.
  * `https://apis.naver.com/searchadvisor/crawl-request/verify.json`

#### API restrictions and precautions
1. When accessing the API, please make sure to use TLS v1.2 or higher protocol. Connection is not possible with TLS 1.0/1.1.

2. The number of URL Submit API calls per affiliate is limited per day. It is deducted based on the number of urls in the payload of the url submit API, and an error message is sent if the amount is used more than the given limit.
If you respond with [Request exceeded message](https://searchadvisor.naver.com/guide/crawl-request-api#exceedingMsg), subsequent requested URLs will not be collected and will be discarded. Please refer to the API response code section.
> In the case of the URL submit API, if you call a large number of URL lists at once, the number of visits from crawlers may temporarily increase. Because this affects the traffic of affiliated sites, we recommend appropriately distributing the number of URL lists and call times when calling APIs. Affiliated users will be able to see the `리포트 -> 제휴 API 현황` menu activated and submit API results in the `URL 업데이트 수` graph. If the update failure number increases, it indicates that collection failed due to a URL error or temporary site failure. Please look at the graph and request appropriate distribution.


### Using URL submit API
The request body (payload) of the submit API is structured as follows.
```json
{
  "urls": [
    {
      "url": "content-location",
      "type": "update"
    },
    {
      "url": "content_location",
      "type": "delete"
    }
  ]
}
```

* urls attribute
  * It is in the form of a list containing a list of URLs to be collected and deleted.
  * **Up to 1,000** sub-urls are allowed.
* url attribute
  * Enter the URL address of the website subject to collection and deletion.
* type attribute
  * update: Naver crawler visits directly and collects and processes the URL.
  * delete: Delete URL information in Naver collection storage. Search robots will not visit the URL for deletion.
* Constraints
  * Payload only allows a maximum of 2MB.
  * If the same URL exists for update and delete, delete takes precedence.
  * We only process affiliated sites in sub-urls.

yes)
```json
{
  "urls": [
    {
      "url": "http://www.your-site.com/article-1",
      "type": "update"
    },
    {
      "url": "http://www.your-site.com/article-2",
      "type": "update"
    },
    {
      "url": "http://www.your-site.com/article-3",
      "type": "delete"
    },
    {
      "url": "http://www.your-site.com/article-4",
      "type": "delete"
    }
  ]
}
```

Example) Transmission example
```
$ curl -v -H "Authorization: Bearer AAAAO...[ACCESS TOKEN 정보]..."\
    -H "Content-Type: application/json"\
    -XPOST https://apis.naver.com/searchadvisor/crawl-request/submit.json\
    -d '{"urls":[{"url":"http://www.your-site.com/article-1","type":"update"},{"url":"http://www.your-site.com/article-4","type":"delete"}]}'
```

  Example) Transmission example (python)
```
...

import requests

submit_api = 'https://apis.naver.com/searchadvisor/crawl-request/submit.json'
headers = {'Content-Type': 'application/json', 'Authorization': 'Bearer AAAAO...[ACCESS TOKEN 정보]...'}
payload = '{"urls":[{"url":"http://www.your-site.com/1","type":"update"},{"url":"http://www.your-site.com/article-4","type":"delete"}]}'

response = requests.post(submit_api, data=payload, headers=headers)
print response.status_code
print response.text

...
```

   Example) Transmission example (java)
```
...

URI apiUrl = new URI("https://apis.naver.com/searchadvisor/crawl-request/");
UriComponents submitUri = UriComponentsBuilder.newInstance().uri(apiUrl).path("submit.json").build();

HttpHeaders headers = new HttpHeaders();
headers.setContentType(MediaType.APPLICATION_JSON_UTF8);
headers.add("Authorization", "Bearer AAAAO...[ACCESS TOKEN 정보]...");
String payload = "{\"urls\": [{\"url\": \"http://www.your-site.com/1\",\"type\": \"update\"}]}";
HttpEntity<String> request = new HttpEntity(payload, headers);

RestTemplate rest = new RestTemplate();
ResponseEntity<String> response = rest.exchange(
        submitUri.toUriString(),
        HttpMethod.POST,
        request,
        String.class);

System.out.println(response.getStatusCode());

...
```
  Example) Transmission example (php)
```
<?php
  /* Bearer 타입의 인증키 정보 및 json header 지정 */
  $auth_header = "Authorization: Bearer AAAAO...[ACCESS TOKEN 정보]...";
  $json_header = "Content-type: application/json";
  /* 수집대상 URL */
  $payload_str = '{
    "urls": [
      {
        "url": "http://www.your-site.com/",
        "type": "update"
      }
    ]
  }';
  $client_opt = array(
    CURLOPT_URL => "https://apis.naver.com/searchadvisor/crawl-request/submit.json", /* 수집요청 API 호출주소 */
    CURLOPT_POST => true, /* POST 방식 */
    CURLOPT_POSTFIELDS => $payload_str, /* 수집대상 URL payload 전달 */
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_CONNECTTIMEOUT => 10,
    CURLOPT_TIMEOUT => 10,
    CURLOPT_HTTPHEADER =>
    /* 헤더에 인증키 정보 추가 */
    array("Host: apis.naver.com", "Pragma: no-cache", "Accept: */*", $auth_header, $json_header)
  );
  $crawl_api = curl_init();
  curl_setopt_array($crawl_api, $client_opt);
  $response = curl_exec($crawl_api);
  curl_close($crawl_api);
  var_dump($response)
 ?>
```

### Using the URL Verify API
The request body (payload) of the verify API is the same as the submit API, and you can verify in advance whether there are any grammar problems in the body.
Example) Transmission example
```
$ curl -v -H "Authorization: Bearer AAAAO...[ACCESS TOKEN 정보]..."\
    -H "Content-Type: application/json"\
    -XPOST https://apis.naver.com/searchadvisor/crawl-request/verify.json\
    -d '{"urls":[{"url":"http://www.your-site.com/article-1","type":"update"},{"url":"http://www.your-site.com/article-4","type":"delete"}]}'
```

Example) Transmission example (python)
```
...

import requests

verify_api = 'https://apis.naver.com/searchadvisor/crawl-request/verify.json'
headers = {'Content-Type': 'application/json', 'Authorization': 'Bearer AAAAO...[ACCESS TOKEN 정보]...'}
payload = '{"urls":[{"url":"http://www.your-site.com/1","type":"update"},{"url":"http://www.your-site.com/article-4","type":"delete"}]}'

response = requests.post(verify_api, data=payload, headers=headers)
print response.status_code
print response.text

...
```

  Example) Transmission example (java)
```
...

URI apiUrl = new URI("https://apis.naver.com/searchadvisor/crawl-request/");
UriComponents verifyUri = UriComponentsBuilder.newInstance().uri(apiUrl).path("verify.json").build();

HttpHeaders headers = new HttpHeaders();
headers.setContentType(MediaType.APPLICATION_JSON_UTF8);
headers.add("Authorization", "Bearer AAAAO...[ACCESS TOKEN 정보]...");
String payload = "{\"urls\": [{\"url\": \"http://www.your-site.com/1\",\"type\": \"update\"}]}";
HttpEntity<String> request = new HttpEntity(payload, headers);

RestTemplate rest = new RestTemplate();
ResponseEntity<String> response = rest.exchange(
        verifyUri.toUriString(),
        HttpMethod.POST,
        request,
        String.class);

System.out.println(response.getStatusCode());

...
```


### API response code
This is the server’s response message when calling the crawl request API.

StatusCode | response code | response message | explanation
----|-----|------|-----
200| 000 | Success	| Transmission was successful. |
400|061 | Malformed url | Incorrectly formatted call URL. |
400|063 | Malformed encoding | Incorrectly formed encoding character. |
400|1001 | Invalid parameter exists in header | Request parameters are invalid. |
400|1002 | Invalid payload. It could not be parsed | The payload data type is invalid. |
401| 024 | Authentication failed | Authentication failed. |
401| 028 | Authentication header not exists | There is no OAuth Header. |
401| 029 | Auth Authentication failed | The requested Authorization value could not be verified. |
401|1003 | Unowned site. Verify site owner at searchadvisor.naver.com | This site has not been verified for ownership. |
401|1004 | Invalid alliance. Apply for alliance user at searchadvisor.naver.com | This is not an affiliated site. |
402|1005 | Exceeding request. The number of requests has been exhausted. | The daily request amount has been exceeded.  |
403|030 | Https protocol is required | Please request via https protocol. |
403|071 | Unsupported return format | Unsupported return format. |
404|051 | Api not exists | The API does not exist. |
404|052 | Partner does not exists | There are no registered partners. |
406|1000 | Not found requestable URL in payload  | Your request failed. |
410|1006 | This alliance type is no longer supported. | This form of partnership is no longer supported. |
413|064| Max post size limit 2MB exceeded. | The maximum post size has exceeded 2MB.|
500|1030 | Server error | API server error. |
500|1031 | Back-end Server error | This is an internal linking server error. |

###### If the transmission is successful, you will receive a response message as below.
* Example) submit.json API
```json
{
	"errorCode": 0,
	"message": "Success",
	"result": {
		"totalDeleteCount": 0,
		"totalUpdateCount": 1,
		"requestDeleteCount": 0,
		"requestUpdateCount": 1
	}
}
```
* Example) verify.json API
```
{
	"errorCode": 0,
	"message": "Success",
	"result": "valid"
}
```
* Example) If the daily request amount is exceeded
```
{
	"errorCode": 1005,
	"message": "Exceeding request. The number of requests has been exhausted.",
	"result": ""
}
```

###### When calling the API with an invalid authentication key, you will receive the following response message.
* Example) submit.json API
```json
{
  "message": "Authentication failed. (인증에 실패했습니다.)",
  "errorCode": "024"
}
```
* Example) verify.json API (if not an affiliate user)
```
{
	"errorCode": 1004,
	"message": "Invalid alliance. Apply for alliance user at searchadvisor.naver.com",
	"result": ""
}
```

### Check the affiliate API status report
The collaborative crawl request API is given a relatively high priority among the entire list of URLs that need to be collected by Naver crawler. Please refer to Report > Affiliate API Status in Webmaster Tools and check whether there are any problems with collection of the URL list requested for collection through API.

Affiliate API status is updated every 24 hours. For more information, please refer to the [Introducing the affiliate API status report](https://blog.naver.com/naver_webmaster/222115472900) post on the webmaster's official blog.
