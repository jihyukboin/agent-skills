# TV series (TVSeries)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-tvseries)

###  TV Series

* Displays information about TV series programs.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMjQ1/MDAxNzkyMDQxMzU0NDQ4.MuH8QHLxwG0DtPb3CWZSeYePwnRABYr887G_f8oZ2HAg.dIcHEWk1-8VRIOvdR-noqxMHqBHnMqPNaq8p0t-z8PQg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_TV%EC%8B%9C%EB%A6%AC%EC%A6%88_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.


### TV Series Markup

#### basic guidelines
* If there are many elements to input in actor/creator, etc., enter the elements you want to expose first.

#### Types and Properties
  [TV Series](https://schema.org/TVSeries) defined by Schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| name |  **essential**  | Please enter the program name. |
| actor |  **essential**  | Please enter the performer's name. Please enter each person individually. |
| creator | Not required | Please enter the director's name. Please enter each person individually. |
| genre | Not required | Please enter the genre of the program. Examples: Comedy, Horror, Drama |
| image | Not required | This is a representative image of the program. Used in ImageObject or URL format. |
| description | Not required | This is a description of the program. Please write content-oriented so that it is not too long. |

* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "TVSeries",
  "name": "네이버 드라마",
  "actor": [
    {
      "@type": "Person",
      "name": "김배우"
    },
    {
      "@type": "Person",
      "name": "최배우"
    }
  ],
  "creator": {
    "@type": "Person",
    "name": "김감독"
  },
  "genre": "드라마",
  "image": {
    "@type": "ImageObject",
    "url": "https://example.com/photos/tvseries.jpg",
     "width": "700",
    "height": "500"
  },
  "description": "네이버 생활을 그린 드라마입니다."
}
</script>
```

* Example implemented in Microdata format
```html
<div itemscope itemtype="https://schema.org/TVSeries">
 <span itemprop="name">네이버 드라마</span>
 <div itemprop="actor" itemscope itemtype="https://schema.org/Person">
   <span itemprop="name">김배우</span>
 </div>
 <div itemprop="actor" itemscope itemtype="https://schema.org/Person">
   <span itemprop="name">최배우</span>
 </div>
 <div  itemprop="creator" itemscope itemtype="https://schema.org/Person">
   <span itemprop="name">김감독</span>
 </div>
 <span itemprop="genre">드라마</span>
 <img itemprop="image" src="https://example.com/photos/tvseries.jpg"/>
 <span itemprop="description">네이버 생활을 그린 드라마입니다.</span>
</div>
```
