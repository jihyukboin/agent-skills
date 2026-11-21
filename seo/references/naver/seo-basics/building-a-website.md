# Building a website

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-basic-create)

#### If the content is the same, please set it to use a single host name and single URL if possible.

1. Avoid creating multiple hostnames/URLs that represent the same content.
    * Using multiple hostnames does not increase your chances of appearing in searches. Identical content will be judged as duplicate.
    * It causes unnecessary Internet traffic, such as duplicate content in the web cache, which hinders crawlers from collecting data effectively.

2. If you must use multiple addresses, please 301 redirect to the canonical address.
    * A canonical address is an address you want people to know about and is a unique address that does not change regardless of the hosting company or platform.
    * If the same content needs to be expressed through multiple addresses due to problems such as maintenance of old services or compatibility, you must redirect to the main address. In particular, if there is a www or not, you must redirect to one depending on your preference.
    * When handling redirects, please use HTTP redirects rather than JavaScript (e.g. document.location = new URL;).
![Representative address](https://searchadvisor-phinf.pstatic.net/MjAxOTA5MjFfMTc2/MDAxNTY5MDM0NDA1OTgz.iUayMo_erQwWTZm17hSp1tjhNrt3iR1wb5XJL7wQa30g.0V1nmr4HxkqvksTGP6SDZHaC3aQULGeWPk47nu0Ns1gg.JPEG/seo-basic-2.jpg)
3. If it is difficult to 301 redirect to the main address, please enter the main address as rel="canonical" when marking up HTML.
    * rel="canonical" information can be written using the \<link\> tag. For more information, refer to the Web Standard HTML Markup Guide.
    * If you specify a representative address, there is a greater chance that your content will be exposed as a representative URL in search results without duplication.

#### Please follow hostname standards. Please do not use underscore characters in the host name.
* The characters allowed for host and domain names are alphabets, numbers, and hyphens (-).
   * The hyphen cannot come first or last. (RFC-952)
   * Even in international DNS, called Hangul domain, underscore cannot be used as a hostname. (RFC-5890, 5891, 5892, 5893)
   * Non-standard domain names may work in loosely compliant web browsers, but may misbehave elsewhere. Additionally, links may be activated incorrectly on social media, etc.
![image](https://searchadvisor-phinf.pstatic.net/MjAxOTA5MjFfNTAg/MDAxNTY5MDM0NDA2MzMz.HWLUJBSK24dd220LtgfZVJ5ltl66aJsZJFRR4yz4Bxwg.WARIJSQcTtZbH__w-omIjTBQv_bDCvta5huXo8NcSGEg.JPEG/seo-basic-3.jpg)

#### Please allow crawlers to visit using robots.txt
1. robots.txt sample and explanation
    * Set to allow access only to Naver crawlers
    ```
    User-agent: Yeti
    Allow: /
    ```
    * Make accessible to robots from all search engines
    ```
    User-agent: *
    Allow: /
    ```
    * Make only the root page of the site accessible
    ```
    User-agent: *
    Disallow: /
    Allow: /$
    ```
    * Please set collection prohibition on web pages that should not be allowed to be visited by crawlers, such as administrator pages and personal information pages. If you set all pages to Disallow collection, no pages on the site will be exposed in search results, so it is recommended that you only set URL patterns that are not subject to collection to Disallow.
    ```
    User-agent: Yeti
    Disallow: /private*/
    ```
    Inform Naver crawler that /private-image, /private-video, etc. should not be collected.

    ```
    User-agent: *
    Disallow: /
    ```
    Notifies all crawlers that all pages are prohibited from being collected.

2. The robots.txt file must be located in root.
    Example) http://www.example.com/robots.txt

3. You can tell the location of sitemap.xml in robots.txt.
```
User-agent: *
Allow: /
Sitemap: http://www.example.com/sitemap.xml
```

4. If there is no robots.txt file, Naver crawler considers all documents on the site to be collected.
    * If possible, we recommend creating a robots.txt file, and for documents that cannot be exposed to search engines, apply a collection prohibition policy using the Disallow syntax.
    * For more detailed information about robots.txt, please refer to [http://www.robotstxt.org/](http://www.robotstxt.org).

#### Please create a sitemap XML file so that you can see the structure of the entire site.
1. What is a sitemap?
    * A sitemap is an XML format file that contains a list of URLs to be collected within a site.
    * You can tell the crawler which pages should be collected within the site.
    * Even if it is already being collected, you can help it collect it better by providing additional information to the crawler.

2. sitemap.xml sample and explanation
    * For detailed information on the site map, please refer to [Sitemap Submission Guide](../website-search-integration/submitting-rss-feeds-and-sitemaps.md).
    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
      <url>
		<loc>http://www.example.com/footer.html</loc>
		<lastmod>2019-08-26T11:16:53+09:00</lastmod>
		<changefreq>weekly</changefreq>
		<priority>0.8</priority>
	  </url>
    </urlset>
    ```

#### Please write the error page in accordance with HTTP regulations.
1. Please keep error pages with meaningful HTTP response codes.
    * Please make the 404 error page a 404 Not Found HTTP response.
    * Please do not redirect to the error page.
    * Please do not just print “Page does not exist” and return HTTP 200 OK.
    * Please make it understandable not only by humans but also by software that complies with HTTP regulations.
![image](https://searchadvisor-phinf.pstatic.net/MjAxOTA5MjFfMjA5/MDAxNTY5MDM0NDIzNjAx.n2yUNncID5fbZRe3d2RTMGtck6XqITP_aeso_HC_c2Mg.2JBRGwEsEe6sOEP6LEGO7S83zBlPdzXMmhHl2dPYeD0g.JPEG/seo-basic-7.jpg)

2. Provide natural error information to site visitors through a custom error page.
    * This is a page that guides users when they enter an incorrect URL or access a page outside of their permissions.
      404 Not Found: No data available. URL was entered incorrectly. This is an old URL.
      403 Forbidden: No permission. It's blocked.
      503 Service Not Available: The server is having a hard time. I can't stand it.
    * Even in the above case, please print only the content and do not return HTTP 200 OK.
![image](https://searchadvisor-phinf.pstatic.net/MjAxOTA5MjFfMjk2/MDAxNTY5MDM0NDI0MDk5.rGfWuLVBfWuee7bdpuwv-kF37uwi76FQl_8n5BGeGa0g.LQ4-zezKKpatc63g8wGa3GVnI-PpRIVoarwQDPvYvmAg.JPEG/seo-basic-8.jpg)

#### Please make the site mobile friendly.
1. responsive website
    * Responsive web is a technique where the web browser automatically adjusts the width of a web document to match the device screen size. Responsive web can deliver content optimized for devices using the same URL regardless of whether it is a desktop or mobile environment. Naver search engine recommends responsive websites. For more information, refer to the mobile usability section of the Web Standard HTML Markup Guide.

2. Separate mobile URL provided
    * If there is a separate mobile site corresponding to your desktop site, you should automatically redirect to the mobile site when a user accesses the desktop site with a mobile web browser. Most web browsers have their own user agent name, so please improve the usability of your site so that it recognizes the mobile environment.
    * Typically, sites that offer separate mobile URLs often offer the same content as their desktop sites. In this case, we recommend explicitly specifying the URL of the desktop site that corresponds 1:1 to the page on the mobile site. For more information, see the Mobile Usability section of the Web Standards HTML Markup Guide.
