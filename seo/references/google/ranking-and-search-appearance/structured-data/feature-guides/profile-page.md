# Profile page ( ProfilePage ) structured data

[Source: Google](https://developers.google.com/search/docs/appearance/structured-data/profile-page)

![An illustration of the discussions and forums feature](https://developers.google.com/static/search/docs/images/discussions-and-forums-rich-result.png)

`ProfilePage` markup is designed for any site where creators (either people or
organizations) share first-hand perspectives. Adding this markup helps Google Search understand
the creators that post in an online community, and show better content from that community in
search results, including the [Discussions and Forums](https://blog.google/products/search/google-search-discussions-forums-news/) feature.

Other structured data features can link to pages with `ProfilePage` markup too. For example,
[Article](article.md)
and [Recipe](recipe.md) structured data have authors,
and there are often several authors present in [discussion forum](discussion-forum.md)
and [Q&A page](q-a.md) structured data.

## How to add structured data

Structured data is a standardized format for providing information about a page and classifying the page
content. If you're new to structured data, you can learn more about
[how structured data works](../understand-how-structured-data-works.md).

Here's an overview of how to build, test, and release structured data.

1. Add the [required properties](https://developers.google.com/search/docs/appearance/structured-data/profile-page#structured-data-type-definitions). Based on the
   format you're using, learn where to [insert structured data on the page](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data#format-placement).
   **Using a CMS?** It may be easier to use a plugin that's integrated into your CMS.

   **Using JavaScript?** Learn how to
   [generate structured data with JavaScript](../generate-structured-data-with-javascript.md).
2. Follow the [guidelines](https://developers.google.com/search/docs/appearance/structured-data/profile-page#guidelines).
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

Here's an example of a profile page with markup:

JSON-LD
[Try it out in the Rich Results Test](https://search.google.com/test/rich-results?utm_campaign=devsite&utm_medium=jsonld&utm_source=profile-page)


```
<html>
  <head>
    <title>Angelo Huff on Cool Forum Platform</title>
    <script type="application/ld+json">
    {
      "@context": "https://schema.org",
      "@type": "ProfilePage",
      "dateCreated": "2024-12-23T12:34:00-05:00",
      "dateModified": "2024-12-26T14:53:00-05:00",
      "mainEntity": {
        "@type": "Person",
        "name": "Angelo Huff",
        "alternateName": "ahuff23",
        "identifier": "123475623",
        "interactionStatistic": [{
          "@type": "InteractionCounter",
          "interactionType": "https://schema.org/FollowAction",
          "userInteractionCount": 1
        },{
          "@type": "InteractionCounter",
          "interactionType": "https://schema.org/LikeAction",
          "userInteractionCount": 5
        }],
        "agentInteractionStatistic": {
          "@type": "InteractionCounter",
          "interactionType": "https://schema.org/WriteAction",
          "userInteractionCount": 2346
        },
        "description": "Defender of Truth",
        "image": "https://example.com/avatars/ahuff23.jpg",
        "sameAs": [
          "https://www.example.com/real-angelo",
          "https://example.com/profile/therealangelohuff"
        ]
      }
    }
    </script>
  </head>
  <body>
  </body>
</html>
```

Microdata
[Try it out in the Rich Results Test](https://search.google.com/test/rich-results?utm_campaign=devsite&utm_medium=microdata&utm_source=profile-page)


<pre><code>&lt;html&gt;&#10;  &lt;head&gt;&#10;    &lt;title&gt;Angelo Huff on Cool Forum Platform&lt;/title&gt;&#10;  &lt;/head&gt;&#10;  &lt;body itemtype=&quot;https://schema.org/ProfilePage&quot; itemscope&gt;&#10;    &lt;meta itemprop=&quot;dateCreated&quot; content=&quot;2024-12-23T12:34:00-05:00&quot; /&gt;&#10;  &#9;&lt;meta itemprop=&quot;dateModified&quot; content=&quot;2024-12-26T14:53:00-05:00&quot; /&gt;&#10;    &lt;div itemprop=&quot;mainEntity&quot; itemtype=&quot;https://schema.org/Person&quot; itemscope&gt;&#10;      &lt;div&gt;&lt;span itemprop=&quot;alternateName&quot; id=&quot;handle&quot;&gt;ahuff23&lt;/span&gt; (&lt;span itemprop=&quot;name&quot; id=&quot;real-name&quot;&gt;Angelo Huff&lt;/span&gt;)&lt;/div&gt;&#10;      &lt;meta itemprop=&quot;identifier&quot; content=&quot;123475623&quot; /&gt;&#10;      &lt;div itemprop=&quot;description&quot;&gt;Defender of Truth&lt;/div&gt;&#10;      &lt;img itemprop=&quot;image&quot; src=&quot;https://example.com/avatars/ahuff23.jpg&quot; /&gt;&#10;      &lt;div&gt;Links: &lt;a itemprop=&quot;sameAs&quot; href=&quot;https://www.therealangelohuff.com&quot;&gt;Home Page&lt;/a&gt;&lt;br&gt;&#10;                  &lt;a itemprop=&quot;sameAs&quot; href=&quot;https://example.com/profile/therealangelohuff&quot;&gt;Other Social Media Site&lt;/a&gt;&lt;/div&gt;&#10;      &lt;div&gt;&lt;span itemprop=&quot;interactionStatistic&quot; itemtype=&quot;https://schema.org/InteractionCounter&quot; itemscope&gt;&#10;              &lt;span itemprop=&quot;userInteractionCount&quot;&gt;5&lt;/span&gt;&#10;              &lt;span itemprop=&quot;interactionType&quot; content=&quot;https://schema.org/LikeAction&quot;&gt;likes&lt;/span&gt;&#10;           &lt;/span&gt;,&#10;           &lt;span itemprop=&quot;interactionStatistic&quot; itemtype=&quot;https://schema.org/InteractionCounter&quot; itemscope&gt;&#10;              &lt;span itemprop=&quot;userInteractionCount&quot;&gt;1&lt;/span&gt;&#10;              &lt;span itemprop=&quot;interactionType&quot; content=&quot;https://schema.org/FollowAction&quot;&gt;follower&lt;/span&gt;&#10;           &lt;/span&gt;, and&#10;           &lt;span itemprop=&quot;agentInteractionStatistic&quot; itemtype=&quot;https://schema.org/InteractionCounter&quot; itemscope&gt;&#10;              &lt;span itemprop=&quot;userInteractionCount&quot;&gt;2346&lt;/span&gt;&#10;              &lt;span itemprop=&quot;interactionType&quot; content=&quot;https://schema.org/WriteAction&quot;&gt;posts&lt;/span&gt;&#10;           &lt;/span&gt;&#10;       &lt;/div&gt;&#10;    &lt;/div&gt;&#10;  &lt;/body&gt;&#10;&lt;/html&gt;</code></pre>

## Guidelines

For your profile page structured data to be eligible for usage in Google Search, you must follow these
guidelines:

- [General structured data guidelines](../structured-data-general-guidelines.md)
- [Search Essentials](../../../search-essentials/overview.md)
- [Content Guidelines](https://developers.google.com/search/docs/appearance/structured-data/profile-page#content-guidelines)
- [Technical Guidelines](https://developers.google.com/search/docs/appearance/structured-data/profile-page#technical-guidelines)

### Content guidelines

- The primary focus of the page must be a single person or organization that is
  affiliated with the overall website. Here are some examples of profile pages:


  **Valid use cases**:

  - A user profile page on a forum or social media site
  - An author page on a news site
  - An "About Me" page on a blog site
  - An employee page on a company website

  **Invalid use cases**:

  - The main home page of a store (usually contains lots of non-profile info)
  - An organization review site (the organization isn't associated with the website)

### Technical guidelines

If the profile page also includes the creator's recent activity, you can include markup
using URLs on those objects to reference the page with the full content and markup. For
example, this is one possible markup structure:

```
{
  "@context": "https://schema.org",
  "@type": "ProfilePage",
  "mainEntity": {
    "@id": "#main-author",
    "@type": "Person",
    "name": "Marlo Smith"
  },
  "hasPart": [{
    "@type": "Article",
    "headline": "Things to see in NJ",
    "url": "https://example.com/things-to-see-nj",
    "datePublished": "2014-02-23T18:34:00Z",
    "author": { "@id": "#main-author" }
  }]
}
```

## Structured data type definitions

You must include the required properties for your structured data to be eligible for display in search
results. You can also include the recommended properties to add more information about your profile pages,
which could provide a better user experience.

### `ProfilePage`

The full definition of `ProfilePage` is available at
[schema.org/ProfilePage](https://schema.org/ProfilePage).

<table>
<colgroup><col/></colgroup>
<thead><tr><th colspan="2">Required properties</th></tr>
</thead>
<tbody>
<tr>
<td>
<code>mainEntity</code>
</td>
<td><p><code><a href="https://schema.org/Person">Person</a></code> or
        <code><a href="https://schema.org/Organization">Organization</a></code></p>
<p>The person or organization that this profile page is about. This indicates that the primary
          focus of this page is information about this entity.</p>
<p>Try to use the correct type if that information is available (meaning, if you know whether
          the page represents an individual or an organization); otherwise, default to <code>Person</code>
          (for example, if it's an unknown type of account).
        </p>
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
<td><code>dateCreated</code></td>
<td>
<p><code><a href="https://schema.org/DateTime">DateTime</a></code></p>
<p>The date and time that the profile was created, if applicable, in
          <a href="https://wikipedia.org/wiki/ISO_8601">ISO 8601</a> date
          format.
        </p>
</td>
</tr>
<tr>
<td><code>dateModified</code></td>
<td>
<p><code><a href="https://schema.org/DateTime">DateTime</a></code></p>
<p>The date and time that information in the profile was modified, if applicable, in
            <a href="https://wikipedia.org/wiki/ISO_8601">ISO 8601</a> date
            format. Ideally, this only represents human-edited metadata changes to the profile (for
            example, adding extra outlinks to places this profile is referenced wouldn't be a
            modification).
          </p>
</td>
</tr>
</tbody>
</table>

### `Person` or `Organization`

Both [schema.org/Person](https://schema.org/Person)
and [schema.org/Organization](https://schema.org/Organization)
share common properties that are used by Google.

<table>
<colgroup><col/></colgroup>
<thead><tr><th colspan="2">Required properties</th></tr></thead>
<tbody>
<tr>
<td><code>name</code></td>
<td>
<p><code><a href="https://schema.org/Text">Text</a></code></p>
<p>The primary way the person or organization is identified. We recommend using this field
          for real names (and <code>alternateName</code> for social media handles). However, you
          can use this field to specify a social media handle if that's the only way the person is
          identified on your site.</p>
<aside>If the <code>name</code> property isn't available, you can provide the
          <code>alternateName</code> property to fulfill this requirement.
      </aside></td>
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
<td><code>agentInteractionStatistic</code></td>
<td>
<p><code><a href="https://schema.org/InteractionCounter">InteractionCounter</a></code></p>
<p>User statistics about the profile page entity's own behavior, if applicable.</p><p>
</p><p>Google recognizes the following <code>interactionTypes</code>:</p>
<ul>
<li><a href="https://schema.org/FollowAction">https://schema.org/FollowAction</a>:
            The number of other accounts being followed.</li>
<li><a href="https://schema.org/LikeAction">https://schema.org/LikeAction</a>:
            The number of likes (generally of other entity's posts).</li>
<li><a href="https://schema.org/WriteAction">https://schema.org/WriteAction</a>:
            The number of posts.</li>
<li><a href="https://schema.org/ShareAction">https://schema.org/ShareAction</a>:
            The number of reshares of posts.</li>
</ul>
</td>
</tr>
<tr>
<td><code>alternateName</code></td>
<td>
<p><code><a href="https://schema.org/Text">Text</a></code></p>
<p>An alternate public identifier, if applicable. For example, a social media handle if
          a person's real name is used in the <code>name</code> field.</p>
</td>
</tr>
<tr>
<td><code>description</code></td>
<td>
<p><code><a href="https://schema.org/Text">Text</a></code></p>
<p>The user's byline or applicable credential, if applicable.</p>
</td>
</tr>
<tr>
<td><code>identifier</code></td>
<td>
<p><code><a href="https://schema.org/Text">Text</a></code></p>
<p>Any unique identifier that's used within your site, if applicable. This could be an
          internal database ID that your site uses to identify a user even if their social media
          handle changes.</p>
</td>
</tr>
<tr>
<td><code>image</code></td>
<td><p><code><a href="https://schema.org/URL">URL</a></code> or
        <code><a href="https://schema.org/ImageObject">ImageObject</a></code></p>
<p>The URL or <code>ImageObject</code> of a profile image of the creator, if applicable. If there are no
          images, don't include a default image, icon, or placeholder image in this field.</p>
<p>Additional image guidelines:
  </p><ul>
<li>Image URLs must be crawlable and indexable. To check if Google can access your URLs, use
      the <a href="https://support.google.com/webmasters/answer/9012289">URL Inspection tool</a>.</li>
<li>Images must represent the marked up content.</li>
<li>Images must be in a file format that's <a href="https://developers.google.com/search/docs/appearance/google-images#supported-image-formats">supported by Google Images</a>.</li>
<li>For best results, we recommend providing multiple high-resolution images (minimum of 50K pixels when
      multiplying width and height) with the following aspect ratios: 16x9, 4x3, and 1x1.</li>
</ul>
<p>For example:</p>
<pre>"image": [
  "https://example.com/photos/1x1/photo.jpg",
  "https://example.com/photos/4x3/photo.jpg",
  "https://example.com/photos/16x9/photo.jpg"
]</pre>
</td>
</tr>
<tr>
<td><code>interactionStatistic</code></td>
<td>
<p><code><a href="https://schema.org/InteractionCounter">InteractionCounter</a></code></p>
<p>User statistics applied to the profile page entity, if applicable. Only include stats
          about the platform that the profile page is hosted on (don't reference that the creator
          also has 100,000 followers on their home page).</p><p>
</p><p>Google recognizes the following <code>interactionTypes</code>:</p>
<ul>
<li><a href="https://schema.org/FollowAction">https://schema.org/FollowAction</a>:
            The number of followers.</li>
<li><a href="https://schema.org/LikeAction">https://schema.org/LikeAction</a>:
            The number of likes of this entity.</li>
<li><a href="https://schema.org/BefriendAction">https://schema.org/BefriendAction</a>:
            A bi-directional relationship.</li>
</ul>
</td>
</tr>
<tr>
<td><code>sameAs</code></td>
<td>
<p><code><a href="https://schema.org/URL">URL</a></code></p>
<p>The URL to other external profiles or home pages for the profile, if applicable.</p>
</td>
</tr>
</tbody>
</table>

## Monitor rich results with Search Console

Search Console is a tool that helps you monitor how your pages perform in Google Search.
You don't have to sign up for Search Console to be included in Google Search results,
but it can help you understand and improve how Google sees your site. We
recommend checking Search Console in the following cases:

1. [After deploying structured data for the first time](https://developers.google.com/search/docs/appearance/structured-data/profile-page#after-deploying)
2. [After releasing new templates or updating your code](https://developers.google.com/search/docs/appearance/structured-data/profile-page#after-releasing)
3. [Analyzing traffic periodically](https://developers.google.com/search/docs/appearance/structured-data/profile-page#analyzing-periodically)

[YouTube video](https://www.youtube.com/watch?v=Vmfvf8nG09k)

### After deploying structured data for the first time

After Google has indexed your pages, look for issues using the relevant
[Rich result status report](https://support.google.com/webmasters/answer/7552505).
Ideally, there will be an increase of valid items, and no increase in invalid items. If you find issues
in your structured data:

1. [Fix the invalid items](https://developers.google.com/search/docs/appearance/structured-data/profile-page#troubleshooting).
2. [Inspect a live URL](https://support.google.com/webmasters/answer/9012289#test_live_page) to check if the issue persists.
3. [Request validation](https://support.google.com/webmasters/answer/13300208) using the status report.

### After releasing new templates or updating your code

When you make significant changes to your website, monitor for increases in structured data invalid items.

- If you see an **increase in invalid items**, perhaps you rolled out a new template that doesn't work, or your site interacts with the existing
  template in a new and bad way.
- If you see a **decrease in valid items** (not matched by an increase in invalid items), perhaps you are
  no longer embedding structured data in your pages. Use the [URL Inspection tool](https://support.google.com/webmasters/answer/9012289) to learn what is causing the issue.

### Analyzing traffic periodically

Analyze your Google Search traffic using the [Performance Report](https://support.google.com/webmasters/answer/7576553).
The data will show you how often your page appears as a rich result in Search, how often users click on it and what is
the average position you appear on search results. You can also automatically pull these
results with the [Search Console API](https://developers.google.com/webmaster-tools/search-console-api-original/v3/how-tos/search_analytics).

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
- Review the [guidelines](https://developers.google.com/search/docs/appearance/structured-data/profile-page#guidelines) again to identify if your content isn't compliant
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
