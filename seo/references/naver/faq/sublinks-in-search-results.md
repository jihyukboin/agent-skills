# Sublinks in search results

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/faq-sublink)

### Q. What is a sublink?

Sublinks automatically analyze the structure of the website so that users can easily navigate to the information they want.
This refers to the part of Naver search results that appears as links above some descriptions.

![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMTkg/MDAxNzkyMDQ5NTM1ODA2.Yxb9F2dSwk86rIR9ATk-YjltZL_1oCwG-Goby_0hD9wg.s3W6Kw0ylAhrDLq0EqtLQb2kxkiRAeZbC1N7CHzXVu0g.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%84%9C%EB%B8%8C%EB%A7%81%ED%81%AC%EB%85%B8%EC%B6%9C.png)

### Q. I would like to know how to expose sublinks.

Sublinks are **automatically** analyzed and displayed by search engines for useful web documents judged by the search engine to include links judged to be user-preferred and structurally important.

Therefore, **no additions are made upon separate request, and the link contents may change at any time.**

In order for search engines to extract good sublinks, you need to create a good foundation for analyzing your website structure.
It may be helpful to check the following.

#### 1. Please adhere to web standards
   * Please avoid using links written in javascript.
       * Do not use fragment (#) URLs (see [JavaScript Search Optimization Guidelines](../advanced-seo/javascript-search-optimization.md) for details)
   * Be sure to include anchor text for the HTML link. Good anchor text gives search engines context about the link.
        `<a href="http://www.example.com">앵커텍스트</a>`
   * Even when using HTML images, be sure to include alternative text (alt), a description of the image.
        `<img src="example.gif" alt="이미지에대한설명">`
   *  [It is not recommended to create images of text content.](../content-guidelines/content-writing-recommendations.md)
   * For other information, please refer to [Webmaster Guidelines](https://searchadvisor.naver.com/guide).

#### 2. Please provide a structured navigation structure and sitemap.
   * GNB (Global Navigation Bar) can be considered the face of a website. Make it easy for users to know what pages or functions your website provides through GNB.

[GNB example from navercorp.com]
![naverGNB](https://searchadvisor-phinf.pstatic.net/MjAyMzExMDlfMTc2/MDAxNjk5NDkyMTMyMzg5.J-Whc_is0VE2pA9056A4Lm-PZiRXSiP9hE6HA6X1ndYg.kTAxj2D2IXhdCMslPYxhv91WQ5E77UKQ3Q7V7LLssN4g.PNG/faq-sublink-new1.png)

### Q. We recently changed the site structure. When will the sublink be updated?

Sublinks can be updated only when the crawler re-collects site information.
However, please note that it takes a certain amount of time (within 7 days on average) to re-collect and reflect the information.

If there has been a site reorganization, please also check to see if access by crawlers is smooth or if anything is partially blocked.


### Q. Sublinks with incorrect information are being exposed. How do I delete it?

If you do not want to expose sublinks, please add the attribute values ​​`` `<a>` ` `태그에  ` ` `rel="nosublink"` ``.
```
<a href="https://www.mysite.com/attend" rel="nosublink">출석체크</a>
```

If you want to exclude **all sublinks** of your site from being displayed in Naver search results, please add the tag `` `meta` `` to the head area of ​​the html as shown below.
```
<head>
<meta name="naver" content="nosublinks">
</head>
```

If deletion is required due to incorrect sublinks or personal information being exposed, you can request deletion through the link below.

[Go to request deletion of incorrect sublink](https://help.naver.com/support/alias/search/site/site_14.naver)

However, partial deletion of the link may not be possible and processing of the request may take time.
If a sublink is deleted due to a report, it may be permanently excluded and cannot be restored, so please set it yourself using the above setting method if possible.
