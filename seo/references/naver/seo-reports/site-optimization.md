# Site optimization

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/report-seo)

### What is a Site Optimization Report?
* The site optimization report covers how to optimize the site and improve its quality so that the content within the site can be properly exposed in Naver's search results according to the search user's intent. The content mentioned in the guide is not dependent on a specific search engine. When developing a site for the first time or reorganizing it, if you only follow the recommendations in web standards, you can naturally achieve the effect of not only helping users who visit your site consume content, but also helping search engines better understand the content structurally.

* This report does not answer how your site can appear at the top of Naver's search results. All web pages must be created primarily for visiting users, and if they are created to be optimized only for search engines, it is difficult to provide a good experience to users whose main purpose is content consumption.

* The site must have quality tailored to the needs of users who visit for its intended purpose. In addition, enjoy the effect of naturally improving the quality of your site by complying with the technical matters recommended by web standards. Naver Search and Webmaster Tools will help you increase the influx of visitors to your site.

* The ranking within site optimization is based on an AI-based evaluation algorithm based on information collected only from sites registered in Webmaster Tools. This indicator is used as an indirect indicator of search ranking, but even if all items are excellent, it does not necessarily rank high in searches. Since there are numerous ranking factors that refer to search rankings in addition to site optimization, the formula that the report's rating is the top search does not apply.


* * *


### Search robot collection
* Representative quality items related to crawler collection are the amount of documents that can be collected according to robot rule settings and the presence of correct XML sitemap and RSS.

* The content of the site displayed in Naver search results is reflected according to logic after the crawler visits the site, collects information, and processes the indexing process. Therefore, it is necessary to correctly specify robot rules specified by web standards so that Naver crawlers can recognize your site and collect content that can be allowed to external users. It is very important to create robot rules by classifying content that should be exposed to searches within your site and content that should not be exposed.

* There are hundreds of millions of sites on the web, and Naver's crawler has limitations in visiting the content of all sites in a short period of time. An XML site map that tells the Naver crawler which pages should be collected within the site is a useful way to help the crawler collect. Additionally, if you use RSS, a web standard, for new posts created within the site, you can more quickly inform the crawler that the latest content is reflected in searches.


* * *


### Content Management
* A representative quality item related to content management is whether the titles and descriptions of web pages are designed to clearly describe the topic of the content.

* The quality of your site title and description is very important in ensuring that your site is recognized by searchers. The site title and description must be written in phrases that represent the content so that users can easily recognize them. Even if the title and description are applied properly, if they are too long and difficult to read at a glance, or if the same keywords are meaninglessly repeated, it may have a detrimental effect on search exposure, so it is recommended to write concisely with content that can well explain the company's brand or service information.

* For more information, see the Content section of the Web Standards HTML Markup Guide.

#### Do not leave the title of your web page blank.
* The title of a web page is important information that appears in the first row of search results. If the site title is empty or there is a quality problem, the search engine automatically extracts the most appropriate information from the page or uses the anchor text linking the page to determine the most appropriate content and exposes it in search results. Please provide a clear and unique title to help searchers find your content.

* For more information, see the Content section of the Web Standards HTML Markup Guide.

#### Don't give every page on your site the same title.
* The title of your web page must be unique. A unique title that matches the content of your page increases the likelihood that searchers will find your content. When a search user enters a search term to search for information, if the contents of your site are listed with the same title, it may be disadvantageous in terms of the user's preference. Creating a unique title that matches the topic of your content is the most important step in improving the quality of your site.

* In Naver's integrated search, use the site: query to enter the address of your site. If the documents displayed in the search results have the same title, you need to check whether the title tag on the web page is empty or filled with the same content.
(Example) Naver domain site: query search results


* * *

### site structure
* A representative quality related to site structure is whether the HTML of the web page is written in a structure that search engines can understand. Even if a web page is filled with great content, if it is expressed in a structure that search engines cannot understand, it may be detrimental to the quality evaluation. Please enlist the help of an expert, such as a site developer, to create HTML appropriate for the structure of your content.

#### Use HTML tags that can express the structure of the content well.
* In the stage of evaluating the structure of collected web pages, Naver search engine separates and interprets HTML tags representing content by item. If we look at representative examples that are not problematic for humans to view in a web browser, but are difficult for machine crawlers to interpret, the following are examples.

* Example of incorrect use of HTML \<head\> tag information
  * When there is no information that can summarize the content of a web document, such as the document title or description tag
  ```
  <title></title>
  <meta name="description" content="">
  ```
  * When the charset attribute of the meta tag is specified differently from the string encoding method provided by the web server.
  ```
  <-- 웹서버는 utf-8 방식의 인코딩을 사용하지만 meta 태그의 charset 값은 euc-kr 인코딩 방식으로 지정-->
  <meta charset="euc-kr">
  ```
* Example of incorrect use of HTML \<body\> tag information
   * If the content is tagged with \<frame\>
     ```
     <frame src="https://webmastertool.naver.com">
     ```
   * When information that should exist in the \<head\> tag is in the \<body\> tag
     ```
     <body>
     <title> 제목은 head 태그 내부에 존재해야 합니다.</title>
     </body>
     ```
   * When JavaScript is used when expressing a link, making interpretation difficult
     ```
     <a href="#" onclick="javascript:goto(A)">웹마스터도구</a>
     ```

#### Please use anchor text in links on your site.
* Site link management is very important not only for site visitors but also for search engines. The anchor text used in the link can help users navigate the desired content within the site, and the search engine understands the implicit content of the linked document through the anchor text and visits the link directly to use it for collection.
* What is anchor text?
  * Text or keywords used in links that introduce other web documents or sites in a web document
    ```
    <a href="https://webmastertool.naver.com/">웹마스터도구</a>
    ```
  * We recommend that you use concise anchor text that best represents the linked document. Appropriate use of anchor text associated with a document has the effect of reducing user bounce rates and increasing document satisfaction. However, you must be careful as you may be penalized in search exposure if you use the same keyword as anchor text for the purpose of ranking at the top of search results.
* What is image alt attribute?
   * Text that can replace an image in environments where the image cannot be displayed in the browser
   ```
   <img src="images/webmaster-main.jpg" alt="웹마스터도구 메인 이미지">
   ```
   * Images in documents can also be expressed as text that can replace the image using the alt attribute. This information can help search engines understand the image and is considered very important information that can be used in image search results. Like anchor text, image alt attributes may be penalized if you use the same text for the purpose of ranking at the top of searches, so please specify clear text that can express the image.


* * *


### Site activation
* Representative quality items related to site activation can be divided into the amount of content reflected in searches and the external reputation of the site. In order to increase the activation index, you must increase the inflow of visitors by continuously publishing content that fits the purpose of the site, and make efforts to promote your site so that it can be naturally cited on authoritative web pages.

#### How to avoid missing web page search reflections
* Even if the site has a lot of content, if the crawler cannot collect and index it, it will not be exposed in searches. It is important to start by submitting an XML sitemap so that crawlers can collect it well, and to configure the links in the document so that search engines can interpret them well.

#### How can I improve my site reputation?
![image](https://searchadvisor-phinf.pstatic.net/MjAxOTA5MjFfMTkx/MDAxNTY5MDM0NDU2MzQ0.eUtXwOJnF7q1uWKF4Ao6qG4NvMeePYIdJyKnJvgRL2Yg.K_YOvYVtoXdVDudQZ6dv5843BReFNhKlu6iQOlGNh_Ag.GIF/site-quality-1.gif)

* While organizing your site's internal links is important, it's most important that your content is linked to on trustworthy external sites. For example, it may be judged that it is more advantageous in terms of reliability if a specific document is mentioned in 10 different sites than if it is mentioned in 10 links on different web pages within the same site. However, you should be careful because if your site is mentioned on a site that was intentionally created to increase the frequency of mentions of external links, you may be penalized in search results.

* There are various ways to mention your site in various services within Naver. Naver provides a variety of free tools that can be used for business purposes and community spaces such as blogs and cafes for free. Please use these services to help your site spread to more users.

* A prerequisite for improving a site's reputation is to continuously maintain quality content that matches the site's purpose. If your quality content is naturally cited on external web pages by site visitors, your site's reputation can naturally improve.
