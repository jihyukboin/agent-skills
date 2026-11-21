# Configuring robots.txt

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-basic-robots)

robots.txt is [international recommendations](http://www.robotstxt.org/robotstxt.html) that allows or restricts crawlers to collect sites and web pages. IETF issued [standardization document](https://www.rfc-editor.org/rfc/rfc9309) for this in September 2022.

The robots.txt file should always be located in the root directory of your site and should be written as a plain text file following [Robot exclusion standards](https://ko.wikipedia.org/wiki/로봇_배제_표준). Naver crawler complies with the rules written in robots.txt, and if there is no robots.txt file in the root directory of the site, it is considered to be able to collect all content.

However, if there is a separate agreement with the webmaster on collection conditions, robots for special purposes such as acquiring advertiser information or creating link previews may not refer to the rules in robots.txt or may not fully comply with them. Therefore, for content that should not be exposed to the outside world, including personal information, you must protect it through other methods, such as a login function, in addition to this setting, or use other blocking methods.

### robots.txt location
 The robots.txt file must be located in the site's root directory and must be accessible as a text/plain file.
 * Example) http://www.example.com/robots.txt

### Processing according to HTTP response code
When the Naver crawler accesses the site's robots.txt, please send the normal 2xx response code. The crawler operates as follows according to [HTTP response code](http-protocol.md).

|  | Response code group |  explanation |
| --- | --- | --- |
| 2xx | Successful | It interprets and uses rules that comply with [Robot exclusion standards](https://ko.wikipedia.org/wiki/로봇_배제_표준). If robots.txt is returned as an HTML document, even if there are valid rules in it, robots.txt may be interpreted as none (all allowed). Therefore, we recommend writing it as a plain text file (text/plain) that follows the robot exclusion rules.  |
| 3xx | Redirection | Up to 5 HTTP redirects are allowed, and if more redirects occur, they are stopped and interpreted as 'allow all'. **Redirections via HTML and JavaScript are not interpreted, so care must be taken.** |
| 4xx | Client Error | Interpreted as ‘allow all’. |
| 5xx | Server Error | Interpreted as ‘disallow all’. However, if there are robots.txt rules that were previously collected normally, they may be used temporarily.  |

### robots.txt rule example
Rules written in the robots.txt file are only effective for pages under the same host, protocol, and port number.  The contents of http://www.example.com/robots.txt do not apply to http://example.com/ and https://example.com/.

Representative rules are as follows, and please change them to suit the nature of the site's content.

* Do not allow collection from robots from other search engines, but only allow collection from crawlers for the Naver search service.
    ```
    User-agent: *
    Disallow: /
    User-agent: Yeti
    Allow: /
    ```
* Set to allow collection for robots from all search engines.
    ```
    User-agent: *
    Allow: /
    ```
* Set only the root page of your site to allow collection.
    ```
    User-agent: *
    Disallow: /
    Allow: /$
    ```
* Please set web pages that should not be visited by crawlers, such as administrator pages and personal information pages, to not allow collection. The example below tells the crawler for the Naver search service that /private-image, /private-video, etc. should not be collected.
    ```
    User-agent: Yeti
    Disallow: /private*/
    ```
* Notifies all crawlers that collection is not permitted for all pages on the site. This example is not recommended because no pages on your site are included in the collection.
    ```
    User-agent: *
    Disallow: /
    ```

### Please allow favicon collection
Search robots consider favicon files to be part of the source web page content. Therefore, even though it is a web page that is basically allowed to be collected by crawlers, if the path containing the embedded favicon is set to robots.txt, there are cases where the robot does not follow the rules and attempts to collect the content.

Therefore, when setting robots.txt, if possible, set the favicon of the document exposed in searches to be the same as the document or allow collection by default to avoid confusion. For more information regarding favicons displayed in searches, please refer to [Favicon Markup Guide](../html-markup/favicon.md).

### Please also check the JavaScript and CSS file paths.
Robots sometimes attempt to access not only HTML web documents, but also other resources included therein, such as JavaScript or CSS, regardless of settings. As the number of documents that are difficult to interpret correctly with HTML alone, or that may be interpreted as completely different from the webmaster's intent unless resources are also accessed and analyzed, is increasing, modern crawlers consider these to be part of web documents that are allowed to be collected.

Therefore, please set the rules to be the same as the web documents that refer to these resource URLs, or allow collection by default. For more information, please refer to the [JavaScript Search Optimization](../advanced-seo/javascript-search-optimization.md) document.

### Specify sitemap.xml
You can help crawlers better collect content from your site by recording the location of [sitemap.xml](../website-search-integration/submitting-rss-feeds-and-sitemaps.md), which contains a list of pages on your site, in robots.txt.

```
User-agent: *
Allow: /
Sitemap: http://www.example.com/sitemap.xml
```

### Use the robots.txt tool in Webmaster Tools.
Using the robots.txt tool provided by Webmaster Tools, you can more easily manage your site's robots.txt file and provides two functions as follows.

#### 1. robots.txt collection and verification
![robots.txt collection and verification](https://searchadvisor-phinf.pstatic.net/MjAxOTExMjlfNDQg/MDAxNTc1MDE2MzU3Mzk3.Y0ZebOLap7xw-U75leHAM3hCrZpcoXThSGTw1IgnfFQg.qwaDMJ3VaQlkkCGylOqEQrzAHm6Yrqhpw5euM_vvwzcg.PNG/seo-basic-robots-1.png)

* If you want to quickly notify crawlers after modifying the robots.txt file in the site's root directory, click Request Collection.
* You can test whether web pages can be collected according to the set robot rules.

#### 2. Simple creation of robots.txt
![Simple creation of robots.txt](https://searchadvisor-phinf.pstatic.net/MjAxOTExMjlfMTc4/MDAxNTc1MDE2MzU4NTIw.UgiyYEYRoIMUV2iFcUc7c8-WHyFfL-nhZkONy_xj2Ykg.CBRDGXXveA6PZVldzlJs0ptvrGcXB1XQsm5CHYi0G4Ug.PNG/seo-basic-robots-2.png)
* You can simply create and download a robots.txt file. If you upload the downloaded robots.txt file to the site's root directory and then execute the crawl request in step 1 above, Naver crawler can immediately recognize it.
