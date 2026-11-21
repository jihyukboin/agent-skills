# JavaScript search optimization

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-advanced-javascript)

Most websites use JavaScript to improve user experience. Recently, as JavaScript technology has advanced, many developers are converting the web to a single page application (SPA) platform by introducing frameworks such as Angular, React, and Vue.js when building sites. Of course, Naver website search also takes these trends into account and supports the crawling and indexing of sites built based on SPA.

In the case of SPA sites, JavaScript plays a leading role in determining the structure of web pages, so Naver crawler also measures and interprets the influence of JavaScript during the collection and content interpretation process. This series of processes requires several times more resources than traditional HTML page interpretation. Therefore, even for SPA sites, it is recommended that main areas of HTML be rendered on the server (Server Side Rendering) so that crawlers can better recognize them.

This guide explains how the Naver crawler processes JavaScript included in the collected HTML. If you are building a site using the SPA method, please refer to the contents of this guide and proceed with JavaScript search optimization.

#### Please check if JavaScript and CSS can be collected.
Sometimes, even though some sites allow crawling of web pages, resource URLs such as JavaScript and CSS are set to not allow collection.
```
User-agent: *
Allow: /your-html-url
Disallow: /your-javascript-url
Disallow: /your-css-url
```
In this case, if access to the web documents that the robot is allowed to collect is essential for accurate interpretation (rendering), there may be confusion in operation. Therefore, please check the contents of robots.txt to match the crawl policy with the web document or allow full collection.
```
User-agent: *
Allow: /your-javascript-url
Allow: /your-css-url

혹은 별도로 지정 하지 않음
```

For reference, when the Naver crawler attempts to collect auxiliary resource information such as JavaScript, a characteristic string (Yeti, etc.) may be added to the browser User-Agent, as shown in the example. The specific version may change at any time. For more detailed information, please refer to [How to check crawler](../seo-basics/verifying-naver-s-crawler.md).
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko; compatible; Yeti/1.1; +https://naver.me/spd) Chrome/W.X.Y.Z Safari/537.36
```

#### Do not use fragment (#) URLs
A fragment is a rule created to specify a specific location within a page.
```
https://www.mysite.com/page#subsection-1
https://www.mysite.com/page#subsection-2
```

Naver crawler removes the fragment part in the process of interpreting the URL to be collected. Therefore, in the case of the URL in the above example, change it to https://www.mysite.com/page and proceed with collection.

If your site URL is constructed as a fragment (#) URL of a single page application (SPA), each
If the URL guarantees independent content, it should be changed to [Permalink](https://ko.wikipedia.org/wiki/퍼머링크).

```
예) fragment (#) 또는 해쉬뱅 (#!) 으로 구축된 URL

https://www.mysite.com/#home
https://www.mysite.com/#product
https://www.mysite.com/path/to/#!/faq-1
https://www.mysite.com/path/to/#!/faq-2
```

```
예) permalink 로 변경

https://www.mysite.com/home
https://www.mysite.com/product
https://www.mysite.com/path/to/faq-1
https://www.mysite.com/path/to/faq-2
```

### Understanding web browser-based interpretation (rendering)
In order to accurately interpret HTML documents allowed for collection, Naver crawler internally renders and analyzes them by adding the resource files mentioned in the same way as the regular web browser you use.

1. When a crawler discovers a page that dynamically processes HTML using JavaScript, it checks whether the JavaScript resources included in the page have been collected.

2. If JavaScript is not collected, the static HTML content is first collected/analyzed and indexed.

3. JavaScript resources included in HTML go through a separate collection process and are stored on the rendering server for a certain period of time. Occasionally, it has been discovered that a timestamp or hash value is added to the JavaScript URL to force the latestness of the resource. This is not recommended as it may cause problems interpreting the content of the page during the collection process.

4. When a crawler revisits the page, if there is any Java script, it renders the HTML including the script and attempts to analyze the content more accurately.

5. After determining whether the main content of the rendering result page has changed, decide whether to update the index.

### Q. Are SPA sites built with JavaScript excluded from search exposure?
In order to efficiently collect numerous web pages existing on the Internet, Naver crawler has a process to determine the “collection priority” for each page. Since the collection resources allocated to the crawler are limited, we select URLs that are considered important algorithmically and then proceed with collection.

Because there are physical limits not only to the crawling of web pages but also to the size of indexing of documents, indexing and search exposure are not guaranteed even if collection has already occurred. Therefore, you should not simply assume that SPA-based sites are not exposed in searches.
