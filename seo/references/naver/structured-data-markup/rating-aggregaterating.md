# Rating (AggregateRating)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-rating)

###  Rating (AggregateRating)

* Displays rating information such as evaluation score and number of ratings/reviews.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMjQ4/MDAxNzkyMDQxMzU3OTAz.kWGG7_fqAD8MGPx0Xd7refdkWXuNmzo6rYKeEJIOFQ4g.1mu43YvGRDUKkC-BqgqbL36Kueh_20SkD_hSD4Xg4hAg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%ED%8F%89%EC%A0%90_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.


### Rating (AggregateRating)

#### basic guidelines
* For pages with multiple ratings, enter the final rating value in AggregateRating.
* Only numbers (integer or decimal) greater than or equal to 0 are allowed. Negative numbers, exponents, text, etc. cannot be used.

#### Types and Properties
  [AggregateRating](https://schema.org/AggregateRating) defined by schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| ratingValue | **essential** | This is a point value representing the rating. |
| bestRating | select   | This is the highest value in the rating system. Must be greater than or equal to the ratingValue value.|
| ratingCount | * [Note 1] | This is the total number of individual ratings that make up the above rating.|
| reviewCount | * [Note 1] | Number of reviews entered with or without a rating  |
  * [Note 1] When displaying a rating, either ratingCount or reviewCount must be included to be displayed. If both exist, the ratingCount value is displayed first.


#### example
* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Product",
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5",
    "bestRating": "5",
    "reviewCount": "10"
    "ratingCount": "10"
  }
}
</script>
```

* Example implemented in Microdata format
```html
<div itemprop="aggregateRating" itemscope itemtype="https://schema.org/AggregateRating">
  <span itemprop="ratingValue">4.5</span>
  <span itemprop="bestRating">5</span>
  <span itemprop="reviewCount">11</span>
  <span itemprop="ratingCount">11</span>
</div>
```
