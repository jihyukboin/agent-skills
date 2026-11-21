# Review (Review)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-review)

###  Review

* Reviews are displayed as text and scores.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMTgw/MDAxNzkyMDQxMzkyOTE5.Pl6xPZVeJ9Do90Gyxs_nM5UBeKNgi3u_P7RU3gSrpf8g.lH84AaBFBJlX4fPJ0X2lyY3F2UGNWgQxZCE4QVInT7cg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EB%A6%AC%EB%B7%B0_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.


### Review

#### basic guidelines
* Individual reviews are written as a Review property under properties such as the product being reviewed.
* Please allow only one review subject per page.
* Negative or exponential notation is not allowed in ratingValue and bestRating.

#### Types and Properties
  [Review](https://schema.org/Review) defined by schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| reviewBody | **essential** | This is the review content. Please exclude meaningless review text that consists only of numbers or special characters. |
| ratingValue | Not required | This is the evaluation score. 0~5 are the default values.|
| bestRating | Not required | This is the highest value in the rating system. If no value is provided, 5 is used as the default value. Must be greater than the ratingValue value.|

* Example implemented in JSON-LD format
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Product",
  "review": [
    {
      "@type": "Review",
      "reviewBody": "마음에 드는 제품입니다.",
      "reviewRating": {
        "@type": "Rating",
        "bestRating": "5",
        "ratingValue": "4"
      }
    },
    {
      "@type": "Review",
      "reviewBody": "판매자분이 매우 친절합니다.",
      "reviewRating": {
        "@type": "Rating",
        "bestRating": "5",
        "ratingValue": "5"
      }
    },
    {
      "@type": "Review",
      "reviewBody": "생각했던 그대로입니다.",
      "reviewRating": {
        "@type": "Rating",
        "bestRating": "5",
        "ratingValue": "3"
      }
    }
  ]
}
</script>
```

* Example implemented in Microdata format
```html
<div itemscope itemtype="https://schema.org/Product">
  <div itemprop="review" itemscope itemtype="https://schema.org/Review">
      <span itemprop="reviewBody">마음에 드는 제품입니다.</span>
      <div itemprop="reviewRating" itemscope itemtype="https://schema.org/Rating">
        <span itemprop="bestRating">5</span>
        <span itemprop="ratingValue">4</span>
      </div>
  </div>
  <div itemprop="review" itemscope itemtype="https://schema.org/Review">
      <span itemprop="reviewBody">판매자분이 매우 친절합니다.</span>
      <div itemprop="reviewRating" itemscope itemtype="https://schema.org/Rating">
        <span itemprop="bestRating">5</span>
        <span itemprop="ratingValue">5</span>
      </div>
  </div>
  <div itemprop="review" itemscope itemtype="https://schema.org/Review">
      <span itemprop="reviewBody">생각했던 그대로입니다.</span>
      <div itemprop="reviewRating" itemscope itemtype="https://schema.org/Rating">
        <span itemprop="bestRating">5</span>
        <span itemprop="ratingValue">3</span>
      </div>
  </div>
</div>
```
