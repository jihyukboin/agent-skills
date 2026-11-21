# Software app ( SoftwareApplication ) structured data

[Source: Google](https://developers.google.com/search/docs/appearance/structured-data/software-app)

Mark up software application information in the body of a web page to better display your app
details in Google Search results.

![Software application rich result in Google Search results](https://developers.google.com/static/search/docs/images/software-apps.png)

**Note**: The actual appearance in search results might be different. You can
preview most features with the
[Rich Results Test](https://support.google.com/webmasters/answer/7445569).

## How to add structured data

Structured data is a standardized format for providing information about a page and classifying the page
content. If you're new to structured data, you can learn more about
[how structured data works](../understand-how-structured-data-works.md).

Here's an overview of how to build, test, and release structured data.

1. Add the [required properties](https://developers.google.com/search/docs/appearance/structured-data/software-app#structured-data-type-definitions). Based on the
   format you're using, learn where to [insert structured data on the page](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data#format-placement).
   **Using a CMS?** It may be easier to use a plugin that's integrated into your CMS.

   **Using JavaScript?** Learn how to
   [generate structured data with JavaScript](../generate-structured-data-with-javascript.md).
2. Follow the [guidelines](https://developers.google.com/search/docs/appearance/structured-data/software-app#guidelines).
3. Validate your code using the
   [Rich Results Test](https://search.google.com/test/rich-results)
   and fix any critical errors. Consider also fixing any non-critical issues that may be flagged
   in the tool, as they can help improve the quality of your structured data (however, this isn't necessary to be eligible for rich results).
4. Deploy a few pages that include your structured data and use the [URL Inspection tool](https://support.google.com/webmasters/answer/9012289) to test how Google sees the page. Be sure that your page is
   accessible to Google and not blocked by a robots.txt file, the `noindex` tag, or
   login requirements. If the page looks okay, you can
   [ask Google to recrawl your URLs](../../../crawling-and-indexing/crawler-management/ask-google-to-recrawl-your-urls.md).
   **Note**: Allow time for re-crawling and re-indexing. Remember that it
   may take several days after publishing a page for Google to find and crawl it.
5. To keep Google informed of future changes, we recommend that you
   [submit a sitemap](../../../crawling-and-indexing/sitemaps/build-and-submit-a-sitemap.md). You can automate this with the
   [Search Console Sitemap API](https://developers.google.com/webmaster-tools/v1/sitemaps).

## Examples

JSON-LD

Here's an example of a software app in JSON-LD:

[Try it out in the Rich Results Test](https://search.google.com/test/rich-results?utm_campaign=devsite&utm_medium=jsonld&utm_source=software-app)


```
<html>
  <head>
    <title>Angry Birds</title>
    <script type="application/ld+json">
    {
      "@context": "https://schema.org",
      "@type": "SoftwareApplication",
      "name": "Angry Birds",
      "operatingSystem": "ANDROID",
      "applicationCategory": "GameApplication",
      "aggregateRating": {
        "@type": "AggregateRating",
        "ratingValue": 4.6,
        "ratingCount": 8864
      },
      "offers": {
        "@type": "Offer",
        "price": 1.00,
        "priceCurrency": "USD"
      }
    }
    </script>
  </head>
  <body>
  </body>
</html>
```

RDFa

Here's an example of a software app in RDFa:

[Try it out in the Rich Results Test](https://search.google.com/test/rich-results?utm_campaign=devsite&utm_medium=rdfa&utm_source=software-app)


<pre><code>&lt;div vocab=&quot;https://schema.org/&quot; typeof=&quot;SoftwareApplication&quot;&gt;&#10;  &lt;span property=&quot;name&quot;&gt;Angry Birds&lt;/span&gt; -&#10;&#10;  REQUIRES &lt;span property=&quot;operatingSystem&quot;&gt;ANDROID&lt;/span&gt;&#10;  TYPE: &lt;span property=&quot;applicationCategory&quot; content=&quot;GameApplication&quot;&gt;Game&lt;/span&gt;&#10;&#10;  RATING:&#10;  &lt;div property=&quot;aggregateRating&quot; typeof=&quot;AggregateRating&quot;&gt;&#10;    &lt;span property=&quot;ratingValue&quot;&gt;4.6&lt;/span&gt; (&#10;    &lt;span property=&quot;ratingCount&quot;&gt;8864&lt;/span&gt; ratings )&#10;  &lt;/div&gt;&#10;&#10;  &lt;div property=&quot;offers&quot; typeof=&quot;Offer&quot;&gt;&#10;    Price: $&lt;span property=&quot;price&quot;&gt;1.00&lt;/span&gt;&#10;    &lt;meta property=&quot;priceCurrency&quot; content=&quot;USD&quot; /&gt;&#10;  &lt;/div&gt;&#10;&lt;/div&gt;&#10;  </code></pre>

Microdata

Here's an example of a software app in Microdata:

[Try it out in the Rich Results Test](https://search.google.com/test/rich-results?utm_campaign=devsite&utm_medium=microdata&utm_source=software-app)


<pre><code>&lt;div itemscope itemtype=&quot;https://schema.org/SoftwareApplication&quot;&gt;&#10;  &lt;span itemprop=&quot;name&quot;&gt;Angry Birds&lt;/span&gt; -&#10;&#10;  REQUIRES &lt;span itemprop=&quot;operatingSystem&quot;&gt;ANDROID&lt;/span&gt;&#10;  TYPE: &lt;span itemprop=&quot;applicationCategory&quot; content=&quot;GameApplication&quot;&gt;Game&lt;/span&gt;&#10;&#10;  RATING:&#10;  &lt;div itemprop=&quot;aggregateRating&quot; itemscope itemtype=&quot;https://schema.org/AggregateRating&quot;&gt;&#10;    &lt;span itemprop=&quot;ratingValue&quot;&gt;4.6&lt;/span&gt; (&#10;    &lt;span itemprop=&quot;ratingCount&quot;&gt;8864&lt;/span&gt; ratings )&#10;  &lt;/div&gt;&#10;&#10;  &lt;div itemprop=&quot;offers&quot; itemscope itemtype=&quot;https://schema.org/Offer&quot;&gt;&#10;    Price: $&lt;span itemprop=&quot;price&quot;&gt;1.00&lt;/span&gt;&#10;    &lt;meta itemprop=&quot;priceCurrency&quot; content=&quot;USD&quot; /&gt;&#10;  &lt;/div&gt;&#10;&lt;/div&gt;&#10;  </code></pre>

## Guidelines

You must follow these guidelines for your app to be eligible to appear as a rich result.

**Warning:** If your site violates one or more of these guidelines,
then Google may take [manual action](https://support.google.com/webmasters/answer/2604824) against it. Once you have remedied the problem, you can submit your site for
[reconsideration](https://support.google.com/webmasters/answer/35843).

- [Search Essentials](../../../search-essentials/overview.md)
- [General structured data guidelines](../structured-data-general-guidelines.md)

## Structured data type definitions

You must include the required properties for your content to be eligible for display as a rich result.
You can also include the recommended properties to add more information about your content,
which could provide a better user experience.

### `SoftwareApplication`

The full definition of `SoftwareApplication` is available at
[schema.org/SoftwareApplication](https://schema.org/SoftwareApplication).

The Google-supported properties are the following:

<table>
<colgroup><col/></colgroup>
<thead>
<tr><th colspan="2">Required properties</th></tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code>
</td>
<td>
<p><code><a href="https://schema.org/Text">Text</a></code></p>
<p>The name of the app.</p>
</td>
</tr>
<tr>
<td>
<code>offers.price</code>
</td>
<td>
<p><code><a href="https://schema.org/Offer">Offer</a></code></p>
<p>An offer to sell the app. For developers, <code>offers</code> can indicate the
              marketplaces that carry the application. For marketplaces, use <code>offers</code> to
              indicate the price of the app for a specific app instance.</p>
<p>
              If the app is available without payment, set <code>offers.price</code> to <code>0</code>. For example:
            </p>
<pre>"offers": {
  "@type": "Offer",
  "price": 0
}</pre>
<p>
              If the app has a price greater than 0, we recommend also including the <code>offers.priceCurrency</code> property (or Google will try to find the right currency).
              For example:
            </p>
<pre>"offers": {
  "@type": "Offer",
  "price": 1.00,
  "priceCurrency": "USD"
}</pre>
</td>
</tr>
<tr>
<td>
            Rating or review
          </td>
<td>
<p>
              A rating or review of the app. You must include one of the following properties:
            </p>
<table>
<tr>
<td>
<code>aggregateRating</code>
</td>
<td><p><code><a href="https://schema.org/AggregateRating">AggregateRating</a></code></p>
<p>The average review score of the app. Follow the
              <a href="https://developers.google.com/search/docs/appearance/structured-data/review-snippet#guidelines">Review snippet
                guidelines</a> and list of required and recommended
              <a href="https://developers.google.com/search/docs/appearance/structured-data/review-snippet#aggregate_rating_type_definitions">AggregateRating properties</a>.</p>
</td>
</tr>
<tr>
<td>
<code>review</code>
</td>
<td><p><code><a href="https://schema.org/Review">Review</a></code></p>
<p>A single review of the app. Follow the
              <a href="https://developers.google.com/search/docs/appearance/structured-data/review-snippet#guidelines">Review snippet
                guidelines</a> and list of required and recommended
              <a href="https://developers.google.com/search/docs/appearance/structured-data/review-snippet#review-properties">Review properties</a>.</p>
</td>
</tr>
</table>
</td>
</tr>
</tbody>
</table>

<table>
<colgroup><col/></colgroup>
<thead>
<tr><th colspan="2">Recommended properties</th></tr>
</thead>
<tbody>
<tr>
<td>
<code>applicationCategory</code>
</td>
<td>
<p><code><a href="https://schema.org/Text">Text</a></code></p>
<p>The type of app (for example, <code>BusinessApplication</code> or
              <code>GameApplication</code>). The value must be a supported app type.</p>
<p><b>List of supported app types</b></p>
<ul>
<li><code>GameApplication</code></li>
<li><code>SocialNetworkingApplication</code></li>
<li><code>TravelApplication</code></li>
<li><code>ShoppingApplication</code></li>
<li><code>SportsApplication</code></li>
<li><code>LifestyleApplication</code></li>
<li><code>BusinessApplication</code></li>
<li><code>DesignApplication</code></li>
<li><code>DeveloperApplication</code></li>
<li><code>DriverApplication</code></li>
<li><code>EducationalApplication</code></li>
<li><code>HealthApplication</code></li>
<li><code>FinanceApplication</code></li>
<li><code>SecurityApplication</code></li>
<li><code>BrowserApplication</code></li>
<li><code>CommunicationApplication</code></li>
<li><code>DesktopEnhancementApplication</code></li>
<li><code>EntertainmentApplication</code></li>
<li><code>MultimediaApplication</code></li>
<li><code>HomeApplication</code></li>
<li><code>UtilitiesApplication</code></li>
<li><code>ReferenceApplication</code></li>
</ul>
</td>
</tr>
<tr>
<td>
<code>operatingSystem</code>
</td>
<td>
<p><code><a href="https://schema.org/Text">Text</a></code></p>
<p>The operating system(s) required to use the app (for example, <code>Windows 7</code>,
              <code>OSX 10.6</code>, <code>Android 1.6</code>)</p>
</td>
</tr>
</tbody>
</table>

### Extended properties for app subtypes

For mobile applications and web applications, Google also supports
[`MobileApplication`](https://schema.org/MobileApplication) and [`WebApplication`](https://schema.org/WebApplication).

Google doesn't show a rich result for Software Apps that only have the [`VideoGame`](https://schema.org/VideoGame) type.
To make sure that your Software App is eligible for display as a rich result, co-type the
[`VideoGame`](https://schema.org/VideoGame)
type with another type. For example:

```
{
  "@context": "https://schema.org",
  "@type": ["VideoGame", "MobileApplication"],
  ....
}
```

## Troubleshooting

If you're having trouble implementing or debugging structured data, here are some resources that
may help you.

- If you're using a content management system (CMS) or someone else is taking care of your site,
  ask them to help you. Make sure to forward any Search Console message that details the issue to them.
- Google does not guarantee that features that consume structured data will show up in search results.
  For a list of common reasons why Google may not show your content in a rich result, see the
  [General Structured Data Guidelines](../structured-data-general-guidelines.md).
- You might have an error in your structured data. Check the
  [list of structured data errors](https://support.google.com/webmasters/answer/13300873)
  and the [Unparsable structured data report](https://support.google.com/webmasters/answer/9166415).
- If you received a structured data manual action against your page, the structured data on
  the page will be ignored (although the page can still appear in Google Search results). To fix
  [structured data issues](https://support.google.com/webmasters/answer/9044175#zippy=%2Cstructured-data-issue), use the [Manual Actions report](https://support.google.com/webmasters/answer/9044175).
- Review the [guidelines](https://developers.google.com/search/docs/appearance/structured-data/software-app#guidelines) again to identify if your content isn't compliant
  with the guidelines. The problem can be caused by either spammy content or spammy markup usage.
  However, the issue may not be a syntax issue, and so the Rich Results Test won't be able to
  identify these issues.
- Structured data issues can affect how your site's content appears in search results. Use this
  [Troubleshoot missing rich results / drop in total rich results](https://support.google.com/webmasters/answer/13300208)
  guide to review a step-by-step approach to identify, fix, and validate these issues in Search Console.
- Allow time for re-crawling and re-indexing. Remember that it may take several days after
  publishing a page for Google to find and crawl it. For general questions about crawling and indexing, check the
  [Google Search crawling and indexing FAQ](https://developers.google.com/search/help/crawling-index-faq).
- Post a question in the [Google Search Central forum](https://support.google.com/webmasters/community).
