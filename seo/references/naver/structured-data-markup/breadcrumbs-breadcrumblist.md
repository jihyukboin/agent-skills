# Breadcrumbs (BreadcrumbList)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-breadcrumb)

###  Site movement path (BreadcrumbList)

* [Site movement path](https://ko.wikipedia.org/wiki/%EC%82%AC%EC%9D%B4%ED%8A%B8_%EC%9D%B4%EB%8F%99_%EA%B2%BD%EB%A1%9C) appears in the search results. It can help searchers understand the location of a web page.

![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMTYz/MDAxNzkyMDUwMzQ1NTE4.oSlk_HNyUPVbrSPZ-XHFbOI1UwqIMghqXHwrHdWpZjwg.hiPHmRAQLzWOjnv8M-R99SfbTUeVbh5qvUKY7I1QDJ8g.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%9D%B4%EB%8F%99%EA%B2%BD%EB%A1%9C.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.

### Site breadcrumb (BreadcrumbList) markup

#### basic guidelines
* Create a hierarchical structure for that page with keywords.
* Please be careful not to include too long text or only numbers or special characters.
* Please enter the information in order, starting from broad and gradually becoming more specific.
      Example) `뉴스 > 스포츠 > 축구`, `국내도서 > 소설 > 한국소설`, `회사소개 > 회사개요 > 핵심가치`
#### Types and Properties
  [BreadcrumbList](https://schema.org/BreadcrumbList) defined by schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| name | **essential** | Please enter text that describes the page well, rather than using general words such as "top" or "home." |
| position | Not required | Number in the hierarchy.  |

* Example implemented in JSON-LD format
```html
<script type="application/ld+json">
{
 "@context": "https://schema.org",
 "@type": "BreadcrumbList",
 "itemListElement":
 [
  {
   "@type": "ListItem",
   "position": 1,
   "item":
   {
    "@id": "https://example.com/news.html",
    "name": "뉴스"
    }
  },
  {
   "@type": "ListItem",
  "position": 2,
  "item":
   {
     "@id": "https://example.com/news/sports.html",
     "name": "스포츠"
   }
  }
 ]
}
</script>
```
* Example implemented in Microdata format
```html
<ol itemscope itemtype="https://schema.org/BreadcrumbList">
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <a itemprop="item" href="https://example.com/news.html">
    <span itemprop="name">뉴스</span></a>
    <meta itemprop="position" content="1" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <a itemprop="item" href="https://example.com/news/sports.html">
    <span itemprop="name">스포츠</span></a>
    <meta itemprop="position" content="2" />
  </li>
</ol>
```
