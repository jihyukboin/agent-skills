# Submitting RSS feeds and sitemaps

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/request-feed)

Naver crawler considers RSS and site maps submitted to Webmaster Tools as “content feeds” and periodically revisits them. Because these content feeds contain the URLs of the site's main content, they can be used as a window to actively inform Naver crawlers of your site's URL. If your site's content exposure is low in Naver search results, we recommend submitting RSS and sitemap feeds.

### RSS (Rich Site Summary)
[RSS](https://ko.wikipedia.org/wiki/RSS) is an XML-based publishing protocol that publishes the site's latest content, including the text. Generally, it is used in a structure where subscribers consume content from the site's RSS feed through an RSS reader, and RSS feeds are mainly provided by news or blog sites.

#### RSS document example
```
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">
  <channel>
    <title>사이트 이름</title>
    <link>http://www.example.com/</link>
    <description>사이트 설명</description>
    <item>
      <title>콘텐츠 게시글 1</title>
      <link>http://www.example.com/article-1.html</link>
      <description>글 내용 전체(또는 일부)</description>
      <pubDate>발행시간</pubDate>
      <guid>http://www.example.com/article-1.html</guid>
    </item>
    <item>
      <title>콘텐츠 게시글 2</title>
      <link>http://www.example.com/article-2.html</link>
      <description>글 내용 전체(또는 일부)</description>
      <pubDate>발행시간</pubDate>
      <guid>http://www.example.com/article-2.html</guid>
    </item>
  </channel>
</rss>
```

#### Precautions when submitting RSS
Webmaster Tools performs basic verification procedures as follows when submitting an RSS feed.

1. The domain of all URLs in the RSS feed must be the same domain as the verified site.
2. item There must be at least 1 item. RSS feeds without published articles cannot be submitted.
3. If the RSS feed size exceeds 10MB, it cannot be submitted.
4. If the response speed is slow when collecting RSS feeds, submissions may be restricted.
5. Please process the text of each item included in the feed to include all content (full text disclosure), not just a portion.

Unfortunately, because RSS feeds contain text, it is difficult to include a large number of URLs. We recommend that you actively use sitemaps rather than RSS.

### Sitemap (Sitemap.xml)
[sitemap](https://en.wikipedia.org/wiki/Sitemaps) is a standard protocol designed to tell crawlers which pages should be collected within a site. By using a sitemap, you can provide crawlers with additional information about your URLs, helping them better gather content on your site.

Because the site map only contains URL information for content, not the main text, it is recommended to include all URLs within the site. The crawler extracts URL information included in the site map, selects URLs to be collected through an internal algorithm, and collects them according to priority.

#### Sitemap document example

A sitemap can contain all URLs of a site. Depending on capacity, you can submit in two formats as shown below.

1. A document containing the URL of the content to be collected as a site map containing the URL to be collected

|element|explanation|Required?|
| --- | --- | --- |
|loc| Collected URL| essential |
|lastmod| Date the page was modified | select |
|changefreq| Page change frequency | select |
|priority| Importance within the site | select |

```
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
	<loc>http://www.example.com/article-1.html</loc>
	<lastmod>2019-08-26T11:16:53+09:00</lastmod>
	<changefreq>weekly</changefreq>
	<priority>0.8</priority>
  </url>
  <url>
	<loc>http://www.example.com/article-2.html</loc>
	<lastmod>2019-08-26T11:16:53+09:00</lastmod>
	<changefreq>weekly</changefreq>
	<priority>0.8</priority>
  </url>
</urlset>
```

2. A sitemap index that contains another sitemap.

Because the sitemap contains all URL information, you can create multiple sitemap documents for each content type or category and then include them using an index document. For example, if there is a lot of content in the site, such as a community site, it is used when it is difficult to include all URLs in a single sitemap, as in number 1.

|element|explanation|Required?|
| --- | --- | --- |
|loc| Sitemap URL | essential |
|lastmod| Date the sitemap was modified | select |

```
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap>
    <loc>http://www.example.com/sitemap-1.xml</loc>
    <lastmod>2016-02-26T18:41:07+09:00</lastmod>
  </sitemap>
  <sitemap>
    <loc>http://www.example.com/sitemap-2.xml</loc>
    <lastmod>2015-05-14T21:06:14+09:00</lastmod>
  </sitemap>
</sitemapindex>
```

#### Precautions when submitting sitemap
Webmaster Tools performs basic verification procedures as follows when submitting a sitemap feed.

1. The domain of all URLs in the sitemap feed must be the same domain as the verified site.
2. If the sitemap feed size exceeds 10MB, it cannot be submitted.
3. A sitemap cannot contain more than 50,000 URLs.
4. If the response speed is slow when collecting sitemaps, submission may be restricted.
