# Control what you share with Google Search

[Source: Google](https://developers.google.com/search/docs/crawling-indexing/control-what-you-share)

Google supports a variety of ways that let site owners control what shows up in Google's
search results. While most people focus on getting their pages indexed, sometimes it's
important to do the opposite: prevent content from appearing in Search. There are a few
reasons you might want to block content from Google Search:

- **To restrict data**: You might have data hosted on your site that you want to show
  only to users who are already on your site. You can block Google from crawling such data so
  it doesn't show up in search results.
  Also keep in mind that certain files published on your site may have metadata that can show
  up in Search.
  [Learn more about keeping redacted information out of Search](redacted-information.md).
- **To hide content of less value to your audience**: Your website might have low quality
  content that shouldn't show up in Search. For example, if your website allows users to
  create content, some of that content might be
  [low quality or even spam](https://developers.google.com/search/docs/essentials/spam-policies#user-generated-spam).
  Allowing indexing of such content may have a negative effect on your site's ranking in
  Google's search results.
- **To have Google focus on your important content**: If you have a very large site (over
  hundreds of thousands of URLs) and pages with less important content, or if you have a lot
  of duplicate content, you might want to prevent Google from crawling the duplicate or less
  important pages in order to focus on your more important content.

## How to block content from Google Search

Here are the main ways to block content from Google Search:

<table>
<tr><th colspan="2">Methods</th></tr>
<tr>
<td>
<h3 id="remove-the-content-from-your-site">Remove the content from your site</h3>
</td>
<td>
<p>
<b>Applicable: all content types</b>
</p>
<p>
        Removing content from your site is the best way to ensure that it won't appear in
        Google Search and anywhere else on the Internet.
      </p>
</td>
</tr>
<tr>
<td>
<h3 id="password-protect-your-files">Password-protect your files</h3>
</td>
<td>
<p>
<b>Applicable: all content types</b>
</p>
<p>
        If you have confidential or private content on your site, you need to password protect
        it to ensure only authorized users can access it. This will also prevent that content
        from appearing in Google Search, or if it already appears, it will eventually remove
        that content from our search results.
      </p>
</td>
</tr>
<tr>
<td>
<h3 id="use-the-noindex-rule">
        Use the <a href="../page-and-content-metadata/meta-tags/noindex.md"><code>noindex</code> rule</a>
</h3>
</td>
<td>
<p>
<b>Applicable: all content types</b>
</p>
<p>
        The <code>noindex</code> robots <code>meta</code> tag is a
        rule that tells Google not to index your content or let it appear in Google Search
        results. Your content can still be linked to and visited through other web pages, or
        directly visited by users with a link, but the content won't appear in Google Search
        results.
      </p>
</td>
</tr>
<tr>
<td>
<h3 id="disallow-crawling-with-robots.txt">
        Disallow crawling with
        <a href="https://developers.google.com/search/docs/crawling-indexing/prevent-images-on-your-page#for-non-emergency-image-removal">robots.txt</a>
</h3>
</td>
<td>
<p>
<b>Applicable: images and video</b>
</p>
<p>
        Google only indexes images and videos that Googlebot is allowed to crawl. To prevent
        Googlebot from accessing your media files, use
        <a href="https://developers.google.com/search/docs/crawling-indexing/prevent-images-on-your-page#for-non-emergency-image-removal">robots.txt rules to block the files</a>.
      </p>
</td>
</tr>
<tr>
<td>
<h3 id="use-robots-meta-tag,-data-nosnippet,-or-x-robots-tag">
        Use robots <code>meta</code> tag, <code>data-nosnippet</code>, or
        <code>X-Robots-Tag</code>
</h3>
</td>
<td>
<p>
<b>Applicable: various content types, depending on the implementation</b>
</p>
<p>
        You can use page- and text-level settings to adjust how Google presents your content in
        search results.
        <a href="../page-and-content-metadata/meta-tags/robots-meta-tag-data-nosnippet-and-x-robots-tag.md">Learn more about <code>meta</code> tags and attributes Google supports</a>.
      </p>
</td>
</tr>
<tr>
<td>
<h3 id="use-the-search-generative-ai-control">Use the Search generative AI control</h3>
</td>
<td>
<p>
<b>Applicable: site-wide</b>
</p>
<p>
        You can manage your site's inclusion in generative AI features on Google Search, including
        AI Overviews and AI Mode, by using the
        <a href="https://support.google.com/webmasters/answer/16908024">Search generative AI control</a>
        in Search Console.
      </p>
</td>
</tr>
<tr>
<td>
<h3 id="opt-out-of-specific-google-properties">
<a href="../../ranking-and-search-appearance/local-features/opting-out-of-local-search-results.md">Opt out of specific Google properties</a>
</h3>
</td>
<td>
<p>
<b>Applicable: web pages</b>
</p>
<p>
        You can tell Google not to include content from your site in specific Google properties,
        such as
        <a href="https://www.google.com/shopping">Google Shopping</a>,
        <a href="https://www.google.com/travel/hotels">Google Hotels</a>, and vacation rentals.
      </p>
</td>
</tr>
</table>

## Remove existing content from Google Search

If the content hosted on your site is already appearing in Google Search, you can request the
removal of those search results. Learn how to
[remove a page hosted on your site from Google Search](page-removals.md).
