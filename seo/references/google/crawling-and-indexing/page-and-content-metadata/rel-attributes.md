# Qualify your outbound links to Google

[Source: Google](https://developers.google.com/search/docs/crawling-indexing/qualify-outbound-links)

For certain links on your site, you might want to tell Google your relationship with the
linked page. In order to do that, use one of the following `rel`
attribute values in the `<a>` tag.

For regular links that you expect Google to fetch and parse without any qualifications, you don't need
to add a `rel` attribute. For example:

```
<p>My favorite horse is the <a href="https://horses.example.com/Palomino">palomino</a>.</p>
```

For other links, use one or more of the following values:

<table>
<colgroup>
<col/>
</colgroup>
<thead>
<tr>
<th colspan="2"><code>rel</code> values</th>
</tr>
</thead>
<tbody>
<tr>
<td><h3 id="sponsored"><code>rel="sponsored"</code></h3></td>
<td>
<p>Mark links that are advertisements or paid placements (commonly called <i>paid
              links</i>) with the <code>sponsored</code> value. Read more about <a href="https://developers.google.com/search/docs/essentials/spam-policies#link-spam">Google's stance on paid links</a>.</p>
<pre>&lt;a <b>rel="sponsored"</b> href="https://cheese.example.com/Appenzeller_cheese"&gt;Appenzeller&lt;/a&gt;</pre>
<aside><b>Note:</b> The <code>nofollow</code> attribute was
              <a href="https://developers.google.com/search/blog/2019/09/evolving-nofollow-new-ways-to-identify">previously recommended</a>
              for these types of links and is still an acceptable way to flag
              them, though <code>sponsored</code> is preferred. </aside>
</td>
</tr>
<tr>
<td><h3 id="ugc"><code>rel="ugc"</code></h3></td>
<td>
<p>We recommend marking user-generated content (UGC) links, such as comments and forum
              posts, with the <code>ugc</code> value.</p>
<pre>&lt;a <b>rel="ugc"</b> href="https://cheese.example.com/Appenzeller_cheese"&gt;Appenzeller&lt;/a&gt;</pre>
<p>If you want to recognize and reward trustworthy contributors, you might remove this
              attribute from links posted by members or users who have consistently made
              high-quality contributions over time. Read more about how to
              <a href="../../monitoring-and-debugging/preventing-and-monitoring-abuse/prevent-user-generated-spam.md">prevent user-generated spam on your site and platform</a>.</p>
</td>
</tr>
<tr>
<td><h3 id="nofollow"><code>rel="nofollow"</code></h3></td>
<td>
<p>Use the <code>nofollow</code> value when other values don't apply, and you'd rather
              Google not associate your site with, or crawl the linked page from, your site. For
              links within your own site, use the
      <a href="https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt#disallow">robots.txt <code>disallow</code> rule</a>.</p>
<pre>&lt;a <b>rel="nofollow"</b> href="https://cheese.example.com/Appenzeller_cheese"&gt;Appenzeller&lt;/a&gt;</pre>
</td>
</tr>
<tr>
<td><h3 id="multiple-values"><i>Multiple values</i></h3></td>
<td>
<p>You may specify multiple <code>rel</code> values as a space- or comma-separated
              list. <b>Examples:</b></p>
<pre>&lt;p&gt;I love &lt;a <b>rel="ugc nofollow"</b> href="https://cheese.example.com/Appenzeller_cheese"&gt;Appenzeller&lt;/a&gt; cheese.&lt;/p&gt;</pre>
<pre>&lt;p&gt;I hate &lt;a <b>rel="ugc,nofollow"</b> href="https://cheese.example.com/blue_cheese"&gt;Blue&lt;/a&gt; cheese.&lt;/p&gt;</pre>
</td>
</tr>
</tbody>
</table>

Links marked with these `rel` attributes will generally not be followed. Remember
that the linked pages may be found through other means, such as sitemaps or links from other
sites, and thus they may still be crawled. These `rel` attributes are used only in
[`<a>` elements that Google can crawl](https://developers.google.com/search/docs/crawling-indexing/links-crawlable#crawlable-links),
except `nofollow`, which is also available as
[robots `meta` tag](meta-tags/meta-tags-and-html-attributes-that-google-supports.md).

If you need to prevent Google from fetching a link to a page on your own site, use the
[robots.txt `disallow` rule](https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt#disallow).

To prevent Google from indexing a page, allow crawling and use the
[`noindex` robots rule](meta-tags/noindex.md).
