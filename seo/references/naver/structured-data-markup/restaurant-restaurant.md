# Restaurant (Restaurant)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-restaurant)

###  Restaurant

* Displays restaurant information.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMTQz/MDAxNzkyMDQxMzcyMjI5.hHsK2KSgzXacOuuGIW7BiVmqFVts0884tClRUtwUPwgg.pIYGu9bYKSVM8scuJNarSS1N32vYu2sMaOtO8PsURkYg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%8B%9D%EB%8B%B9_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.


### Restaurant markup

#### basic guidelines
* Please enter concise information focusing on numbers instead of descriptive text.

#### Types and Properties
  [Restaurant](https://schema.org/Restaurant) defined by Schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| name |  **essential**  | Please enter the name of the restaurant. |
| openingHours |  **essential**  | Please enter business hours information such as day/time. You can enter multiple entries.
| telephone | Not required | Please enter your full phone number including area code. |
| image | Not required | Please enter a representative image of your restaurant. Used in ImageObject or URL format. |
| url | Not required | Please enter the restaurant web page address. Please use the URL format and enter an absolute path, not a relative path or shortened URL. |
| servesCuisine | Not required | Please enter the restaurant's menu. If there are multiple entries, please enter them one by one. |
| priceRange | Not required | Please enter price range information. If you have currency information such as won/dollar, please enter it as well. |
| description | Not required | This is a description of the restaurant. Please write content-oriented so that it is not too long. |

* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Restaurant",
  "name": "네이버 식당",
  "openingHours": [
    "평일 11:00am - 19:00pm",
    "주말 12:00pm - 19:00pm"
  ],
  "telephone": "(031) 784-1000",
  "image": {
    "@type": "ImageObject",
    "url": "https://example.com/photos/restaurant.jpg",
    "width": "700",
    "height": "500"
  },
  "url": "https://www.navercorp.com",
  "servesCuisine": [
    "김치찌개",
    "된장찌개",
    "고등어 구이"
  ],
  "priceRange": "6,000원 ~ 8,000원",
  "description": "한식 전문점입니다."
}
</script>
```

* Example implemented in Microdata format
```html
<div itemscope itemtype="https://schema.org/Restaurant">
  <span itemprop="name">네이버 식당</span>
  <meta itemprop="openingHours" content="평일 11:00am - 19:00pm" />
  <meta itemprop="openingHours" content="주말 12:00pm - 19:00pm" />
  <span itemprop="telephone">(031) 784-1000</span>
  <img itemprop="image" src="https://example.com/photos/restaurant.jpg" />
  <a itemprop="url" href="https://www.navercorp.com">https://www.navercorp.com</a>
  <span itemprop="servesCuisine">김치찌개</span>
  <span itemprop="servesCuisine">된장찌개</span>
  <span itemprop="servesCuisine">고등어 구이</span>
  <span itemprop="priceRange">6,000원 ~ 8,000원</span>
 <span itemprop="description">한식 전문점입니다.</span>
</div>
```
