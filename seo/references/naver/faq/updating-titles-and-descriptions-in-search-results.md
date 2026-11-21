# Updating titles and descriptions in search results

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/faq-serpedit)

### Q. The information displayed in Naver web search is incorrect.

Information exposed in web searches is **information automatically collected and analyzed by a crawler and cannot be arbitrarily modified by Naver.**

Therefore, the site operator must directly edit the information for the changes to be reflected.
If you are the administrator of the site, please refer to the help below and make corrections yourself.

▶  [Go to page title and description markup guide](../html-markup/content-markup.md)

In particular, if robot collection is not possible or smooth in whole or in part, information updating or analysis may not be smooth. Please check to ensure smooth collection.

#### About URL

The search engine analyzes the collected documents moment by moment, organizes documents that have the same content or are redirected to the same page, extracts representative pages, and provides them as search results. In this case, a URL not set by the site administrator may be selected, and Naver cannot modify it arbitrarily.

However, you can inform the search engine of the URL you want to represent by using [Specify preferred URL](../html-markup/preferred-urls-and-robots-meta-tags.md) as reference information, and deleting unnecessary redirects or duplicate documents from the operating server can also help improve the URL.

#### About the title, site name, and description

Search engines basically analyze and use the title tag information contained in the document and elements that can be viewed as titles on the page.

However, in order to improve search quality and expose results more effectively due to policy, in cases where multiple pages with the same title or description are found, when the engine may determine that the search is not specific and concise, or when robot collection is impeded or incomplete, anchor information (such as mentions on other pages) or other text on the page may be used to provide information.

If possible, it would be helpful to refer to [Tips for writing titles and descriptions](../html-markup/content-markup.md) in the content markup guidelines.


#### About images

In order to improve satisfaction with search results, search engines may analyze document content and automatically display unique thumbnail images if they determine that it is appropriate to display them as well.

However, since the displayed images are the result of automatic analysis by the engine, artificial exposure is difficult, and the webmaster's preference may not be displayed. In particular, images must be collected by a robot separately from the web document to be analyzed/exposed, so when modifying the content, it may take time to reflect it separately from the web document.

Additionally, in addition to the text, Open Graph image tags may also be used in the analysis, and you can refer to the related items in [Content Markup Guide](../html-markup/content-markup.md).



### Q. Is there a difference between the OG (Open Graph) title and description tags and the basic title and description tags? How are these two tags used in Naver web search?

The tags referenced within the HTML document are different.
Both refer to the site name/description and become the title and description that the web page exposes in search results.

#### 1. site title
- Site name: This is the `<title>페이지 제목</title>` tag within the tag of the HTML document.
- Open Graph Title: `<meta property="og:title" content="페이지 제목">` meta information within the tag of the HTML document.

#### 2. Site Description
- Site description: This is `<meta name="description" content="페이지 설명">` meta information within the tag of the HTML document.
- Open Graph Description: This is `<meta property="og:description" content="페이지 설명">` meta information within the tag of an HTML document.

In Naver Web Search, if the site title and description are different from the Open Graph title and Open Graph description, **values ​​optimized for search** are selected during the indexing process and reflected in the search results.
