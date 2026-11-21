# Moving a website

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-basic-migration)

#### Considerations for Site Relocation
* When migrating a site, depending on the size of the content (number of URLs), you need to decide whether to migrate all at once or move by specific category. For small to medium-sized sites, we recommend moving all URLs at the same time. When changing the main address due to a domain change, it is important to use HTTP redirect to ensure that you can move to the new site when accessing the old site.
![Site transfer](https://searchadvisor-phinf.pstatic.net/MjAxOTA5MjFfMTQx/MDAxNTY5MDM0NDM3NzQz.00q0InPQAc_gUbl20MOsi9CXIdnvKUgTfq3kL4Rqndwg.9MxwHXOUfqaF_BJpItrRYt2calV8JKPR-nJWMRauLk0g.PNG/seo-basic-12.png)
* A change in domain or host name means that the main address of the site changes, so search results may change for a certain period of time. It takes time for the quality index evaluated by site A to be propagated to the newly changed site B, and during that time, the Naver crawler recognizes all changed URLs and evaluates their quality. Frequently changing the site's main address will affect the site quality evaluation index, so consider relocating the site only when absolutely necessary, such as changing the brand.

#### Procedure for site transfer
1. Move content from old site to new site.
   * Please make sure that images and files included in the content can also be moved to the new site.

2. Assign a domain to your new site.
    * It may take at least 2-3 days for the crawler to recognize the changed domain. For information regarding domain settings, please check the DNS settings provided by your domain provider.
    * Enter the changed site address in the simple site check of Webmaster Tools. Check whether the site connection (HTTP protocol) is checked normally.

3. Allow all robots.txt of the new site and set 301 HTTP redirect to the new site when accessing the URL of the old site.
   * Naver’s crawler begins collecting content for the new site.
   * Redirect from the old site to the new site uses HTTP redirect. Content redirects must correspond 1:1 based on URL.
   * Assign [Preferred URL](../html-markup/preferred-urls-and-robots-meta-tags.md) (canonical url) to all pages of the new site. This action prevents the new site's search URL from being specified as the old site's domain.

4. Register a new site in Webmaster Tools and submit a sitemap (sitemap.xml).
   * After verifying site ownership, check the crawling and indexing status of the new site.
   * Naver's crawler needs time to collect key content for the new site.
   * The quality evaluation of a site can naturally rise to the level of the old site over time.

5. Closing the old site.
   * If content from the old site is displayed in search results, use Webmaster Tools' web page crawl request to recognize it as the URL of the new site.
   * If there is no influx of users to the old site, shut down the server and delete the old site registered in Webmaster Tools.


#### Note

**Caution: Do not set robots.txt on the old site first or stop or block the server's network first until the transfer is complete**

robots.txt is a setting that blocks further access by crawlers and does not indicate that the document has been changed or disappeared.

In other words, in order to check whether the site or document has been changed or moved to another location, the robot must visit the site and check.
If robots.txt, etc. is set in front, even access to check it is blocked, so the desired operation may not work.

In addition, if the server's network is unconditionally stopped or blocked at the network level, as above, the robot cannot determine whether the server is still operating or whether it is a temporary error.
It may not be possible to reflect what you want.

We recommend that you check that all major pages are changed/not exposed and then set robots.txt, etc.
