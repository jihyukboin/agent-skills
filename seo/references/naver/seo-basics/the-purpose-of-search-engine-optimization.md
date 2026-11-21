# The purpose of search engine optimization

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-basic-intro)

Search engine optimization is the process of organizing content information on your site so that search engines can better understand it. Through this work, you can take steps to ensure that content on your site is not omitted from Naver's search results, and most importantly, you can clearly inform Naver's search engine of the content that users want.

Naver Search gives preference to search engine-friendly sites. Read this guide carefully and check whether your site is optimized for search engines. Naver Search and Webmaster Tools will help you increase the influx of visitors to your site. Use the 10 optimization methods below to reflect your site content in Naver searches.

#### 1. Register your site in Webmaster Tools and verify ownership.
* Site registration is supported on a per-host basis only.
    * http://www.mysite.com  (O)
    * http://blog.mysite.com  (O)
    * http://www.mysite.com/myid  (X)
* Site ownership can be verified using HTML meta tags or uploading an HTML file. If you do not have permission to edit HTML or are unable to upload files to the site, please contact the site's technical staff.

#### 2. If you cannot confirm ownership of the site, please check the situations below.
* Please check whether the site's firewall blocks Naver crawlers.
* Support is not available if the site's main page is redirected using JavaScript or the [meta refresh](https://search.naver.com/search.naver?where=nexearch&query=+meta+refresh+&sm=top_hty&fbm=1&ie=utf8) technique.  Please use the [HTTP redirect](https://search.naver.com/search.naver?nso=&page=2&query=HTTP+redirect&sm=tab_pge&start=1&where=web) method.
* If an HTML tag for ownership confirmation is inserted inside the frame tag, support is not possible. Please enter the HTML tag for ownership confirmation outside the frame tag.
* If the original HTML file for upload provided when verifying ownership is damaged, support is not possible.
* Webmaster Tools does not support versions lower than Internet Explorer 11.
* For a more detailed explanation, please refer to the [Verify you own the site](https://help.naver.com/service/30010/contents/17591) section of Naver Customer Center.

#### 3. Please allow Naver crawlers to access the site.
* To allow Naver crawlers to access site documents, set robots.txt as shown below. If it is difficult to change robots.txt yourself, you will need help from the site's technical staff, such as the site creator or developer. For a detailed explanation of robots.txt, see [Setting up robots.txt](configuring-robots-txt.md).

(Example) Set to allow access only to Naver crawlers
```
User-agent: Yeti
Allow: /
```
(Example) Enable access to robots from all search engines
```
User-agent: *
Allow: /
```
* Please allow Naver crawler access on your web server or firewall. The name (User-Agent) of Naver’s crawler is Yeti. (Specific versions may change without notice.)
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko; compatible; Yeti/1.1; +https://naver.me/spd) Chrome/W.X.Y.Z Safari/537.36

또는

Mozilla/5.0 (compatible; Yeti/1.1; +https://naver.me/spd)
```
* If you must block a crawler, do not block it based on IP. The crawler's IP band may change at any time. We recommend using the standard robots.txt method to control access to crawlers. For information on how to check the IP band and name of the Naver crawler, please refer to the [How to check crawler](verifying-naver-s-crawler.md) guide.

#### 4. Please check for duplicate content.
* In order to increase search exposure, multiple sites with the same content may be opened. Please note that in this case, you may be penalized for search exposure.
* Don't use the same title on all pages. The title of the page should contain a phrase that accurately describes the topic of the content. For more information, please refer to [HTML Markup Guide](../html-markup/content-markup.md).

#### 5. Please submit your sitemap and RSS to Webmaster Tools.
* A sitemap is an XML format file that contains a list of URLs to be collected within a site. You can submit a sitemap in XML format from the “Request-Sitemap Submission” menu in Webmaster Tools.
* Please include the latest posts on the site, including the entire text, in the RSS feed. You can submit your RSS feed through the "Request - Submit RSS" menu in Webmaster Tools.
* For more information, please refer to the [Submit RSS and sitemap](../website-search-integration/submitting-rss-feeds-and-sitemaps.md) guide.

#### 6. Please tell us which channels are related to the site.
* A channel is a page for each social media account you run, such as Naver Blog, Cafe, Facebook, and Instagram. Please use [Channel information markup](../structured-data-markup/channels-associated-with-a-site.md) for your online branding.

#### 7. Check Naver search results.
* After Naver's crawler visits, the site's content will be reflected in searches within up to one week. Enter the site name in the Naver search box. Additionally, by using the site: query when searching web documents, you can check whether content from a specific site is reflected in the search.
Example) site:www.mysite.com
* Use the [Content exposure and clicks](../seo-reports/content-impressions-and-clicks.md) report provided by Webmaster Tools to check how exposed and clicked your registered website is in Naver search results.

#### 8. If the site’s main page is not visible in searches
* Please double-check your robots.txt and firewall settings to see if your site allows access to Naver crawlers.
* If there is noindex processing in the meta tag of the main page, turn it off. Pages marked with noindex are excluded from search results.
  (Exceptionally, sites with a public nature such as public institutions, educational institutions, etc. and sites with high user preference may be reflected in searches according to internal policies)
```
<meta name="robots" content="noindex">
```
* Site titles and descriptions are strictly managed by search engines, so please refer to [HTML Markup Guide](../html-markup/content-markup.md) again to check if there are any items that violate the policy.
* Make sure that the information on the site's main page is surrounded by HTML frame tags. Due to the problems caused by the frame tag, it is recommended to use regular HTML tags instead of the frame tag on important pages such as the site's main page.

#### 9. If the site content is not reflected in searches
* If there is noindex processing in the meta tag of the page, turn it off. Pages marked with noindex are excluded from search results.
* Make sure all content on the page is loaded with JavaScript. Most search engines recommend using standard HTML markup to serve your content.
* Make sure all content on the page is wrapped in HTML frame tags. We recommend using regular HTML tags instead of frame tags for important content on the page.
* When loading the page, check if it is redirected using JavaScript. If possible, we recommend using HTTP redirect or meta refresh within the HTML head tag.

#### 10. If the number of documents on the site reflected in Naver search results is small, check the links on the page.
* Please check that the sitemap and RSS submitted to Webmaster Tools are displayed correctly. In particular, if the link in the submitted sitemap and RSS is specified as a relative path, collection will not proceed if the host of the link does not match the registered site.
* If there is nofollow processing in the meta tag of the page, turn it off. For pages marked nofollow, we do not collect links within the page.
```
<meta name="robots" content="nofollow">
```
* If only JavaScript is used when processing links to pages, there is a problem in that the crawler cannot accurately determine which URL it is, so it cannot find other good information later. In order to inform Naver's crawler of your site's internal pages, we recommend providing link URL information that meets standards.
```
<a href="http://www.A.com">Link</a>
해당 링크가 어떤 URL 인지 정확하게 확인할 수 있음
```

```
<span onClick="javascript:goto(A)">Link</span>
대상 링크가 자바스크립트 함수로만 표현되어 있어서 검색로봇은 해당 링크의 정확한 URL을 파악할 수 없음
```
