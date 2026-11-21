# About AMP on Google Search

[Source: Google](https://developers.google.com/search/docs/crawling-indexing/amp)

Google Search indexes [AMP](https://developers.google.com/amp)
pages just like other web pages, and applies the same standard to all pages, regardless of
the technology used to build the page. This page covers how AMP pages appear in Search results,
guidelines for using AMP with Google Search, and common questions about AMP and Google Search. For
more information on the benefits of using AMP, see the
[AMP Project success stories](https://amp.dev/success-stories/).

## How AMP pages can appear in Search results

AMP pages can appear in Google Search as a [rich result](../../ranking-and-search-appearance/structured-data/feature-guides/all-structured-data-features.md),
just like other pages on the web. To help Google better understand your page, you can add
[structured data](../../ranking-and-search-appearance/structured-data/understand-how-structured-data-works.md) to your page. Adding structured data doesn't guarantee that your page appears as a rich
result in Search results. For more information, refer to the
[Structured Data General Guidelines](https://developers.google.com/search/docs/guides/sd-policies).

AMP pages can also appear as Web Stories. Learn more about how to
[enable Web Stories on Google Search](../../ranking-and-search-appearance/web-stories/enable-web-stories-on-google.md).

## Guidelines for AMP pages on Google Search

All of our [best practices for making a site Google-friendly](../../seo-fundamentals/seo-starter-guide.md)
also apply to AMP. This section covers additional guidelines that are specific to AMP on Google Search.

- Your AMP page must follow the [AMP
  HTML specification](https://www.ampproject.org/docs/reference/spec.html). If you're just getting started, learn how to
  [create your first AMP HTML page](https://www.ampproject.org/docs/get_started/create.html).
- Users must be able to experience the same content and complete the same actions on AMP
  pages as on the corresponding canonical pages, where possible.
- Your AMP URL scheme makes sense to the user.
  For example, if your canonical page is `example.com/giraffes`,
  host the AMP somewhere like `amp.example.com/giraffes` or
  `example.com/amp/giraffes`, rather than at `test.com/giraffes`.
  This is because when users click a link to your AMP page from Google Search, the AMP URL
  is visible to the user in the browser (like any web page), and showing a URL that is
  completely unrelated to your main website can be confusing to users.
- Your AMP page must be [valid](https://search.google.com/test/amp)
  so that your pages work as expected for users.
- If you add structured data to your page, make sure that you follow our
  [structured data policies](../../ranking-and-search-appearance/structured-data/structured-data-general-guidelines.md).

## Additional AMP topics

The following topics describe how to work with AMP in Google Search.

<table>
<tr>
<th colspan="2">Topics</th>
</tr>
<tr>
<td><a href="enhance-amp-content.md">Enhance your AMP content in Google Search</a></td>
<td>Learn how to enhance and monitor your AMP pages.</td>
</tr>
<tr>
<td><a href="validate-amp-content.md">Validate your AMP content</a></td>
<td>This document contains tips and pointers about how to validate AMP pages.</td>
</tr>
<tr>
<td><a href="remove-amp-content.md">Remove your AMP pages from Google Search</a></td>
<td>Learn how to remove your AMP pages from Google Search.</td>
</tr>
</table>

## FAQs

### Are AMP pages mobile-only?

No. Since AMP pages can be viewed on all device types, build your AMP pages with
[responsive
design](https://www.ampproject.org/docs/guides/author-develop/responsive_amp).

### How does AMP look on desktop?

AMP pages display equally well on both mobile and desktop screens. If AMP supports all the
functionality that you need, you might consider creating your pages as
[standalone
AMP pages](https://www.ampproject.org/docs/guides/deploy/discovery#what-if-i-only-have-one-page) to support both desktop and mobile visitors for the same page. However, AMP
on desktop doesn't get search-specific features in Google Search results.
