# Google Search's guidance on using generative AI content on your website

[Source: Google](https://developers.google.com/search/docs/fundamentals/using-gen-ai-content)

Generative AI can be particularly useful when researching a topic, and to add structure to
original content. However, using generative AI tools or other similar tools to generate many pages
without adding value for users may violate [Google's spam policy on scaled content abuse](https://developers.google.com/search/docs/essentials/spam-policies#scaled-content).
If you're using generative AI content on your website, **make sure your work meets the
standards of the [Search Essentials](../../search-essentials/overview.md) and our
[spam policies](https://developers.google.com/search/docs/essentials/spam-policies#scaled-content).**

You might find value in looking at the [Search Quality Raters guidelines](https://static.googleusercontent.com/media/guidelines.raterhub.com/en//searchqualityevaluatorguidelines.pdf)
on how to evaluate both scaled content abuse (section 4.6.5) and main content created with little
to no effort, little to no originality, and little to no added value (section 4.6.6). These
guidelines are not a guide to ranking first in Google; they're used by our
[search raters](https://support.google.com/websearch/answer/9281931)
to help evaluate the performance of our [various search ranking systems](../../ranking-and-search-appearance/ranking-systems/a-guide-to-google-search-ranking-systems.md),
and their ratings don't directly influence ranking.

### Focus on accuracy, quality, and relevance

When creating content for the web, focus on accuracy, quality, and relevance, especially when
automatically generating the content. Keep in mind that generative models don't retrieve facts,
but predict a likely sequence of words based on their training data. Because of this, generative
AI outputs may contain inaccuracies (also known as hallucinations). It is critical to manually
factcheck and review all AI-generated content for accuracy and trustworthiness before publishing.
This review also applies to metadata like
[`<title>` elements](../../ranking-and-search-appearance/title-links.md),
[meta description elements](../../ranking-and-search-appearance/snippets.md),
[structured data](../../ranking-and-search-appearance/structured-data/understand-how-structured-data-works.md), and
[alternate texts for images](https://developers.google.com/tech-writing/accessibility/self-study/write-alt-text),
which can appear in Search results.

For structured data, also ensure compliance with the [general guidelines](../../ranking-and-search-appearance/structured-data/structured-data-general-guidelines.md),
the specific policies for the individual search features, and [validate the markup](../../ranking-and-search-appearance/structured-data/structured-data-general-guidelines.md)
to ensure eligibility for [Search features](../../ranking-and-search-appearance/structured-data/feature-guides/all-structured-data-features.md).

### Give users context

Sharing [information about how a piece of content was created](https://developers.google.com/search/docs/fundamentals/creating-helpful-content#how-the-content-was-created)
can help give your readers more context. If you're automatically generating content, consider
adding information on how your content was created in a way that makes sense for your audience,
such as by providing more background information on how automation was used and adding
[image metadata](https://developers.google.com/search/docs/appearance/structured-data/image-license-metadata#add-metadata).

For ecommerce sites, Google Merchant Center has [policies for AI-generated content](https://support.google.com/merchants/answer/14743464).
In particular, AI-generated images must contain metadata using the IPTC `DigitalSourceType`
[`TrainedAlgorithmicMedia`](https://cv.iptc.org/newscodes/digitalsourcetype/trainedAlgorithmicMedia)
metadata. AI-generated product data such as title and description attributes must be specified
separately and labeled as AI-generated.

For more, see our [FAQs in our blog post on AI-generated content](https://developers.google.com/search/blog/2023/02/google-search-and-ai-content).
