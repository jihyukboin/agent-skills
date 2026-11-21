# Improving site indexing efficiency

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-advanced-indexing)

If your web content has been collected by Naver's crawler and delivered to the search engine, the document is included as a candidate for indexing. However, not all collected documents are indexed, and unusable documents deemed unnecessary for indexing are excluded from indexing as shown below. Below is a representative example of an unusable document. We hope that this will be resolved through site improvement to improve indexing efficiency.

#### If there is no HTML content
A typical web page consists of HTML markup, CSS and Image resources, and JavaScript. When Naver crawler interprets the content of a web page, it interprets and processes it in the same way as the latest web browser (rendering) as much as possible.

In the case of certain web pages, there are cases where pure JavaScript is used to move the web page without HTML markup. In this case, the Naver crawler may not be able to interpret it properly and may consider it a web page without content and exclude it from the index.  As mentioned in [Web page navigation guide](../seo-basics/moving-a-web-page.md), it is recommended to use 301 or 302 of [HTTP response code](../seo-basics/http-protocol.md) rather than JavaScript.

#### Soft 404 (or Soft Dead)
When building and operating a site, it is very important to maintain the correct [HTTP response code](../seo-basics/http-protocol.md) for error pages. For example, if an exceptional error situation occurs on the site as shown below, an appropriate guidance page must be provided to the user and an HTTP response code must be specified for each case.

* No data, incorrect URL input, old URL: 404 (Not Found)
* Page available only to logged in users: 403 (Forbidden)
* Site moved to another domain: 301 (Moved Permanently)

The following situations may occur while operating a site. In the cases below, you must also specify an appropriate HTTP response code for each case.

* Site Inspection: 503 (Service Unavailable)
* When the web hosting deadline expires and the site is no longer operational: 503 (Service Unavailable)

If you specify HTTP response code 200 (OK) in the above error situation, the crawler will recognize it as normal web content, collect it, and deliver it to the indexing target. If a case of an invalid document is detected during the indexing process, it is naturally excluded from the index. However, in some cases, it is not recognized as an invalid document and is exposed in searches. Since the content is a document of no help to search users, it can have a negative impact on the reliability of the site.
