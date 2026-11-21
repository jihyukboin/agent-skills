# Requesting crawling and exclusion from search

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/request-crawl)

### Webpage Collection Policy
The web page crawl request provided by Webmaster Tools is a function that allows users to directly request collection of major web pages of a site that the crawler has not yet visited. Collection requests can be made within a limited range for each site.

After requesting collection, visiting the URL and proceeding with collection is a process that incurs a lot of cost. In the same way as the algorithm-driven crawler collection process, the collection of individual URLs requested by users through Webmaster Tools also operates based on priority. Therefore, even if the user directly requests to collect web pages, the crawler does not visit the requested URL in real time.

Once the crawl request URL you requested in Webmaster Tools is delivered to the collection system, it may take at least 1 day to several weeks depending on priority. Therefore, there is no need to repeatedly submit collection requests for the same URL every day. Even if the processing results change due to collection suspension, the crawler may collect the URL through a different route. However, in this case, it is not reflected in the crawl request results of Webmaster Tools.

The crawl request function of Webmaster Tools only serves as a helper to deliver the collection target URL to the collection system. Also, even if collection is successful, there is no guarantee that it will be exposed in Naver's search results. If you improve the quality of your site and your content is cited on other sites, crawlers will naturally recognize this and visit you.
We recommend natural collection by crawlers rather than artificial processing of collection requests.

Sometimes spammers register a large number of spam sites and then [Abusing collection requests](https://blog.naver.com/naver_webmaster/221320610480). To this end, Webmaster Tools is strengthening monitoring of collection requests and limiting collection requests from sites judged to be spam through its own algorithm.

### Excluding webpage searches
Web page search exclusion provided by Webmaster Tools is a function that excludes specific content within a site from the index of the Naver search engine. The process of excluding specific content from searches requires “re-indexing,” so it is not reflected in real time.

1. Please delete the original content of the site first.
2. In Webmaster Tools > Site > Verification > Web Page Optimization, check that when the crawler accesses the deleted document, it is designated as [http response code is 404 Not Found](../seo-basics/http-protocol.md).
3. Please enter the URL to be deleted in Webmaster Tools > Site > Request > Web page search exclusion.
4. As the index information is updated, the document is excluded from the search results.
