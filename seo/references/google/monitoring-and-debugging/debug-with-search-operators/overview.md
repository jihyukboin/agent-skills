# Overview of Google search operators

[Source: Google](https://developers.google.com/search/docs/monitor-debug/search-operators)

Google Search supports
[several search operators](https://support.google.com/websearch/answer/2466433)
that you can use to refine or target your searches. The following search operators may also be
useful for debugging your website.

For example, the `site:` search operator may be useful to monitor comment spam on
your website, and the image search `imagesize:` operator may be helpful to find
images on your site that are small.

Because search operators are bound by indexing and retrieval limits, the
[URL Inspection](https://support.google.com/webmasters/answer/9012289)
tool in Search Console is more reliable for debugging purposes.

The following table contains the search operators that you can use to inspect different aspects of
your pages in Search:

<table>
<thead>
<tr>
<th colspan="2">Search operators</th>
</tr>
</thead>
<tbody>
<tr>
<td><h2 id="filetype:"><code>filetype:</code></h2></td>
<td>
<p>
            Find search results in a
            <a href="../../crawling-and-indexing/file-types-google-can-index.md">specific file type</a>
            as defined by the <code>content-type</code> HTTP header, or file extension.
            For example, you can search for RTF files and URLs ending in <code>.rtf</code> whose
            content contains the term "galway":
          </p>
<pre>filetype:rtf galway</pre>
</td>
</tr>
<tr>
<td><h2 id="imagesize:"><a href="https://developers.google.com/search/docs/monitor-debug/search-operators/image-search#imagesize"><code>imagesize:</code></a></h2></td>
<td>
<p>
            Find pages that contain images of a specific dimension. This search operator only works on Google Images. For example:
          </p>
<pre>imagesize:1200x800</pre>
</td>
</tr>
<tr>
<td><h2 id="site:"><a href="site-search-operator.md"><code>site:</code></a></h2></td>
<td>
<p>
            Find search results from a particular domain, URL, or URL prefix. For example:
          </p>
<pre>site:https://www.google.com/</pre>
</td>
</tr>
<tr>
<td><h2 id="src:"><a href="https://developers.google.com/search/docs/monitor-debug/search-operators/image-search#src"><code>src:</code></a></h2></td>
<td>
<p>Find pages that reference a particular image URL in the <code>src</code> attribute. This search operator only works on Google Images. For example:</p>
<pre>src:https://www.example.com/images/peanut-butter.png</pre>
</td>
</tr>
</tbody>
</table>
