# Pages missing from web search

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/faq-serpmissing)

### First, check if my site is indexed in Naver.
Search for site:site URL in the Naver search bar.

yes)
`
site: https://www.example.com
`

![site search](https://searchadvisor-phinf.pstatic.net/MjAyMDEwMzBfMjEz/MDAxNjA0MDMwNjQwMzk5.sYYeuIcVuoOpIl02-rDn3SgeLdFEMbCz8KKKxti1FUcg.eDFF3BPtpaVp8l0apvb4Rn8D0lTiso3yYHP3u-lyBZIg.PNG/faq-serpmissing-1.png)

#### site: What if the site appears when you search?
This means that Naver has recognized your site, collected your pages, and indexed them.

#### site: What if the site is not visible when you search?
There is a possibility that the Naver crawler has not yet collected the document, or that it is a document that cannot be collected/indexed for various reasons contrary to what is visible.

Due to the nature of collection with a limited number of robots compared to the vast number of web documents on the Internet, there may be cases where collection or information update is not sufficient.
In particular, for sites that have just been created, Naver may not yet know whether the site exists.
If possible, it may be helpful to let us know that the site exists by registering the site in Webmaster Tools and verifying ownership.

Additionally, the website may be in an environment where collection/reflection is difficult, such as through firewall controls, not allowing exposure to search engines, or making it difficult to collect essential page components.
It may be helpful to check information related to the site through a simple site check on Search Advisor.

### Q. My site is not exposed on Naver. Why is that?

If your site is not listed in search results, it may not be exposed for a variety of reasons.
Please check if the reason below applies.

* There may be a disallow collection within robots.txt or noindex meta tag within the document, or a disallow robot collection HTTP header ( [X-Robots-Tag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Robots-Tag) ) set on the web server.
  In particular, if [main resource file](../advanced-seo/managing-resources-and-links.md) cannot be collected in addition to core documents, exposure may be affected.
* There may be restrictions set on the server so that Naver's crawler cannot access the site through the firewall.  [Search robot verification guide](../seo-basics/verifying-naver-s-crawler.md)
* The site may not be developed according to web standards. In particular, we recommend that you carry out web standard optimization work such as setting representative URLs.
* There is a possibility that duplicate documents are reflected in different addresses. Please also check whether the site or document is posted on another URL or other search database of integrated search.
* The content quality may not be suitable for search results. Aren’t you dealing with adult content or illegal information? Or, is the bulletin board on your site not managed properly and filled with spam documents?  Please refer to [Web content spam cases](../content-guidelines/examples-of-web-content-spam.md) to check examples that may be classified as spam.
