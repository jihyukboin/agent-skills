# Manage your sitemaps with a sitemap index file

[Source: Google](https://developers.google.com/search/docs/crawling-indexing/sitemaps/large-sitemaps)

If you have a sitemap that exceeds the
[size limits](build-and-submit-a-sitemap.md),
you'll need to split up your large sitemap into multiple sitemaps such that each new sitemap
is below the size limit. Once you've split up your sitemap, you can use a sitemap index file
as a way to submit many sitemaps at once.

## Sitemap index best practices

The XML format of a sitemap index file is very
similar to the XML format of a sitemap file, and it's defined by the
[Sitemap Protocol](https://www.sitemaps.org/protocol.html#index).
This means that all the sitemap requirements apply to sitemap index files also.

The referenced sitemaps must be hosted on the same site as your sitemap index file. This
requirement is waived if you set up
[cross-site submission](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap#cross-submit).

Sitemaps that are referenced in the sitemap index file must be in the same
directory as the sitemap index file, or lower in the site hierarchy. For example, if the
sitemap index file is at `https://example.com/public/sitemap_index.xml`, it can
only contain sitemaps that are in the same or deeper directory, like
`https://example.com/public/shared/...`.

You can submit up to 500 sitemap index files for each site in your Search Console account.

## Example sitemap index

The following example shows a sitemap index in XML format that lists two sitemaps:

```
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap>
    <loc>https://www.example.com/sitemap1.xml.gz</loc>
    <lastmod>2024-08-15</lastmod>
  </sitemap>
  <sitemap>
    <loc>https://www.example.com/sitemap2.xml.gz</loc>
    <lastmod>2022-06-05</lastmod>
  </sitemap>
</sitemapindex>
```

## Sitemap index reference

The sitemap index tags are defined by the same namespace as generic sitemaps:
[`http://www.sitemaps.org/schemas/sitemap/0.9`](http://www.sitemaps.org/schemas/sitemap/0.9)

To make sure Google can use your sitemap index, you must use the following required tags:

<table>
<tr><th colspan="2">Required tags</th></tr>
<tr>
<td><code>sitemapindex</code></td>
<td>The root tag of the XML tree. It contains all the other tags.</td>
</tr>
<tr>
<td><code>sitemap</code></td>
<td>
      The parent tag for each sitemap listed in the file. It's the only direct child of the <code>sitemapindex</code>
      tag.
    </td>
</tr>
<tr>
<td><code>loc</code></td>
<td>
      The location (URL) of the sitemap. It's a child of the <code>sitemap</code> tag. A sitemap
      index file may have up to 50,000 <code>loc</code> tags.
    </td>
</tr>
</table>

Additionally, the following optional tags may help Google schedule your sitemaps for crawling:

<table>
<tr><th colspan="2">Optional tags</th></tr>
<tr>
<td><code>lastmod</code></td>
<td>
      Identifies the time that the corresponding sitemap file was modified. It
      can be a child of a <code>sitemap</code> tag. The value for the <code>lastmod</code> tag must be in
      <a href="https://www.w3.org/TR/NOTE-datetime">W3C Datetime format</a>.
    </td>
</tr>
</table>

## Troubleshooting sitemaps

If you're having trouble with your sitemap, you can investigate the errors with Google Search Console.
See Search Console's
[sitemaps troubleshooting guide](https://support.google.com/webmasters/answer/7451001#errors)
for help.

## Additional resources

Want to learn more? Check out the following resources:

- [Submit your sitemap to Google](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap#addsitemap)
- [Learn how to combine sitemap extensions](sitemap-extensions/combining-sitemap-extensions.md)
