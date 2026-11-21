# Site diagnostics

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/report-diagnosis)

The site diagnosis information provided by Webmaster Tools is a report that provides problems that occur while Naver's crawler collects site content and the search engine indexes it.

### Site diagnosis status
![image](https://searchadvisor-phinf.pstatic.net/MjAyMjEwMjVfMjc4/MDAxNjY2Njg3MjExMzY3.mC07Ll8f0WYjuhJEOra1QaytNrm931-QWVw408ZdR70g.rn28N8Z-E1kkZT-oJUA6KORJrV2ZYQUg3Ajcm25ITAIg.PNG/report-diagnosis-1.PNG)

* Index: The number of documents collected and indexed normally.
* Collection limit: This is the number of documents whose collection is restricted by page status during the crawler's collection process.
* Index exclusion: This is the number of documents that were collected normally but excluded from the indexing process.
* SEO: Among the collected documents, this is the number of documents that require search engine optimization.

Diagnosis types other than indexing provide detailed information in URL units, so please refer to the guide for each type and proceed with SEO work.
`(사이트 진단은 최근 90일간 수집된 페이지로 분석합니다. 수집, 분석이 완료되어야 페이지 업데이트 결과가 사이트 진단에 반영됩니다.)`

#### index
This is the number of documents collected and processed normally; individual URL information is not provided. Documents that have been indexed are documents that can be exposed to search if they are suitable for the user's query, and can be considered as the number of documents that are actually subject to search. For documents subject to indexing, individual URL information is not provided.

You can check whether a site's content is indexed or not by using a URL search in the Naver search box (e.g., [site:searchadvisor.naver.com](https://search.naver.com/search.naver?where=webkr&sm=tab_jum&query=site:searchadvisor.naver.com)). However, because documents exposed through URL searches only show the current index results, it is not possible to know the increase or decrease in the number of content indexes on my site by period.

You can check whether the number of indexes increases or decreases by period in Webmaster Tools' Site Report > Site Diagnosis. However, because this indicator extracts statistical information at the time the search engine periodically performs indexing, it may differ from the number of indexes displayed through URL searches.

If your site is experiencing declining index counts at some point, consider the following:
* Check whether the site is optimized for search by referring to the collection status. If the number of collected documents has drastically decreased compared to the previous point, the indexing target may be reduced.
* Check whether [noindex in robot meta tag](../html-markup/preferred-urls-and-robots-meta-tags.md) is specified in the markup of the web page.
* Check whether your site complies with [Content Guidelines](../content-guidelines/content-writing-recommendations.md).

#### Collection restrictions
This type of problem occurs during the crawler collection process and occurs because the site's web page operation is not optimized for crawlers. However, pages intended by the site developer (robots.txt, 3xx, 4xx, etc.) are also included, so please analyze the reported content for each type according to the site situation.

Typical types related to collection restrictions are as follows.
* [redirect issue](../seo-basics/moving-a-web-page.md)
* [robots.txt issues](../seo-basics/configuring-robots-txt.md)
* [HTTP protocol issue](../seo-basics/http-protocol.md)

#### Excluding index
This is a type that was collected but occurred during the indexing process, and most cases include problems with the site's HTML markup. In addition, the indexing process also excludes [Spam documents and unused documents](../content-guidelines/examples-of-web-content-spam.md) in accordance with various internal policies.

The representative types related to index exclusion are as follows.
* [Representative URL issues](../html-markup/preferred-urls-and-robots-meta-tags.md)
* [Pages with no HTML content or soft 404s](../advanced-seo/improving-site-indexing-efficiency.md)

#### SEO
Among the collected documents, documents requiring search engine optimization were found. You may be penalized for some elements that are not optimized by the internal algorithm.
SEO-related types are as follows:
* [Title and description problems](../advanced-seo/seo-basics.md)
* [Resource access issues](../advanced-seo/managing-resources-and-links.md)


### Diagnosis History
![image](https://beta-searchadvisor.ssl.phinf.net/MjAyMjEwMjRfMjE1/MDAxNjY2NTgxMjQ5NTA5._r8hHhZvwzOaILuv15B3am5dyyCTzytxVus055EzB-gg.6lUOWcjqzvi8CMohq54wEW45wT2UG2SPOOu3QsDnZm4g.PNG/report-diagnosis-2.PNG)

The diagnosis history shows the amount of change in the URL of the site that the Naver search engine stores and categorizes as daily snapshots during a given period. The most important index amount is expressed in a line graph, and collection restrictions and index exclusions are expressed in a bar graph.

If the collection limit and index exclusion volume is greater than the index volume, please proceed with SEO work by referring to the detailed URL information for each type of diagnosis status above.

### Details by diagnosis type
If you click diagnosis information by type on the diagnosis status screen, you can view the individual diagnosis type trend and URL list as shown below. Up to 2,000 URL lists can be downloaded based on the latest date.

Please refer to the webmaster guide mentioned for each type and proceed with search engine optimization work.

![image](https://searchadvisor-phinf.pstatic.net/MjAyNDA3MTBfNjMg/MDAxNzIwNjAwMTg3NDEz.o4nloBiIkPi7dw6Pftl0JMHrpChbT2GGYpUjeF1mv2Qg.VXKdz-eIvmWixkRMYnJYstM4YuV-CHalTp4_1_VUsZ4g.PNG/seo-diagnosis-detail2.png)

### FAQ
#### Q. The contents of the site diagnosis report are not visible.
**After confirmation of site ownership**, if there is no history of abuse and the site is active and has a lot of content, it will take at least a week for the report to be generated. Additionally, since content from at least one site must be collected to create a report, please proceed with [Search Engine Optimization](../seo-basics/the-purpose-of-search-engine-optimization.md) and [Site reputation management](site-optimization.md) first.

#### Q. There have been no changes despite checking the diagnostic information for collection restrictions, index exclusion, and SEO and reorganizing them according to the guidelines.
Even if the site has been maintained according to the guidelines, the crawler must collect the URL to update the diagnostic information. Please wait until the Naver crawler returns. If you need to re-collect important content, please use [Crawl request](../website-search-integration/requesting-crawling-and-exclusion-from-search.md).
