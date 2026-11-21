# Managing resources and links

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/resource-and-link)

We will guide you through several optimization factors to ensure smooth site collection by Naver crawler.

### Please check if there are any resources with restricted access.
Rather than being composed solely of HTML, modern web documents sometimes require the loading of additional resources (such as javascript) to express and interpret the content of the page.

However, unlike web documents that are allowed to be collected, if these resources exist in a separate URL path, there may be cases where robots.txt is set separately or access is not possible due to IP blocking.
In this case, depending on the situation, the web page cannot be properly analyzed (rendered) and may be displayed differently or not in search results.

#### When access is disabled by robots.txt
We will explain the following URLs A, B, and C as an example.
Naver crawler accesses URL A and collects it. In the A URL HTML document, B and C URLs are added as resources, and B and C URLs are required to compose the A URL content.
However, if you look at robots.txt, `/resource` is disallowed.
In this case, depending on the situation, the robot may collect only C URLs, and the A URL content may be interpreted as incomplete.

```
A. https://www.your-site.com/
B. https://www.your-site.com/resource/1
C. https://www.your-site.com/temp/c


robots.txt)

User-agent: *
Allow: /
Disallow: /resource

```

This behavioral confusion can be resolved by changing the conflicting `disallow: /resource` settings in the default web document to allow, or by modifying the page to consist entirely of the A URL content without the B URL.


#### In case of Naver crawler IP blocking
Check the crawler IP and unblock it through the [How to check Naver crawler](../seo-basics/verifying-naver-s-crawler.md) guide.


### Calling JavaScript on the href attribute of the `<a>` element
`<a>` inserted into the content is an important element.
Naver crawler discovers and collects URLs of other pages on the site using the href attribute in `<a>` and expands them.
If a javascript call is entered in the href attribute, the site collection volume may decrease because a normal link cannot be configured and a new page URL cannot be discovered.
```
나쁜 예 : <a href="createLink(1, news)">클릭</a>
좋은 예 : <a href="https://www.your-site.com/news/1">클릭</a>
```


### Existence of internal links with different protocols

HTTPS sites with security certificates may insert resource links using the same HOST but different protocols (or vice versa).
I suggest changing the resource URL to the same URL protocol.

yes)
A.  https://www.your-site.com/
B. Change **http**://www.your-site.com/resource/1 -> **https**://www.your-site.com/resource/1
