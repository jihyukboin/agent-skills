# Crawl statistics

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/report-crawl-refine)

The content of the website you operate goes through the stages of “collection - refining - indexing - ranking” and is delivered to search users through the Naver search box. The crawling and indexing status provided by Webmaster Tools is a report that you must check before your website is exposed to Naver searches.

### Collection status
No matter how good a website is with content, if it cannot collect, which is the first step of search reflection, it will not be able to proceed to the subsequent search steps.

If collection is not going well, there may be a problem with [Search Engine Optimization](../seo-basics/the-purpose-of-search-engine-optimization.md) on your site. Please refer to the major collection error types and manage your site so that crawlers can recognize them well.

| error type | explanation |
| -| - |
| Robots not allowed | This is a case where collection is disallowed in the [robots.txt](../seo-basics/configuring-robots-txt.md) rule. |
| DNS error | Domain not found. Please check if there is a problem with your domain registration or DNS settings.|
| Connection failed | Please check if TIMEOUT occurs because the web server connection takes a long time or is not working. |
| server error | An error occurred in the web server.  Please check if 4xx, 5xx errors, etc. occur in [HTTP response code](../seo-basics/http-protocol.md). |
| page error | This is a non-existent web page error.  Please check if [HTTP response code](../seo-basics/http-protocol.md) is 404.|
| content error | Sometimes web page content cannot be interpreted.  Please refer to the [HTML markup](../html-markup/content-markup.md) and [JavaScript Search Optimization](../advanced-seo/javascript-search-optimization.md) guides. Please also check whether any important resources included are robot-disallowed or errors are occurring.|
| URL error | Please check if the URL format is abnormal and does not fit [standard](https://en.wikipedia.org/wiki/URL).|
| Pages that take a long time to download | If the site or transmission is so slow that collection attempts take more than a minute for a single document, an error may occur. |
| Pages with large download sizes | This may occur if the HTML document size is large (e.g. 4MB or more). |
