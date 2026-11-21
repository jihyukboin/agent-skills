# Movie (Movie)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-movie)

### Movie

* Displays movie information.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfNzUg/MDAxNzkyMDQxMzY4NzI0.qMth0F3mfG8YsELnRErJ1KdCgJUnqwSvsed-G32q6n8g.5b53Llp3pgLUzq55VejSMDyPLRmrwv20kDTTDdeiuOcg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%98%81%ED%99%94_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.


### Movie markup

#### basic guidelines
* If there are many elements to input in actor/director/genre, etc., enter the elements you want to expose first.

#### Types and Properties
  [Movie](https://schema.org/Movie) defined by Schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| name |  **essential**  | Please enter the movie name. |
| actor |  **essential**  | Please enter the performer's name. Please enter each person individually. |
| director | Not required | Please enter the director's name. Please enter each person individually. |
| genre | Not required | Please enter the genre of the movie. If there are multiple entries, please enter them one by one. Examples: science fiction, action, romance |
| image | Not required | This is a representative image from the movie. Used in ImageObject or URL format. |
| description | Not required | This is a description of the movie. Please write content-oriented so that it is not too long. |

* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Movie",
  "name": "네이버 스릴러",
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
  "director": {
    "@type": "Person",
    "name": "김감독"
  },
  "genre": [
    "스릴러"
  ],
  "image": {
    "@type": "ImageObject",
    "url": "https://example.com/photos/movie.jpg",
     "width": "700",
    "height": "500"
  },
  "description": "네이버 생활을 그린 영화입니다."
}
</script>
```

* Example implemented in Microdata format
```html
<div itemscope itemtype="https://schema.org/Movie">
 <span itemprop="name">네이버 스릴러</span>
 <div itemprop="actor" itemscope itemtype="https://schema.org/Person">
   <span itemprop="name">김배우</span>
 </div>
 <div itemprop="actor" itemscope itemtype="https://schema.org/Person">
   <span itemprop="name">최배우</span>
 </div>
 <div  itemprop="director" itemscope itemtype="https://schema.org/Person">
   <span itemprop="name">김감독</span>
 </div>
 <span itemprop="genre">스릴러</span>
 <img itemprop="image" src="https://example.com/photos/movie.jpg"/>
 <span itemprop="description">네이버 생활을 그린 영화입니다.</span>
</div>
```
