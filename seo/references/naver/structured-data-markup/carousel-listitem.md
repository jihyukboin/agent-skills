# Carousel (ListItem)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-carousel)

###  Carousel (ListItem)

* List-type data is displayed in carousel form.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMjcx/MDAxNzkyMDQxMzYxNDc1.P9WmvtrnXiXTHxL64aWJ6LSoVvClLkxycYDhExhACUEg.GJR1DnRY3GQyJBhj_XkAB_bDYAVQko1uTdynvL4V2GYg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%BA%90%EB%9F%AC%EC%85%80_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.

### Carousel (ListItem) markup

#### basic guidelines
* {name, image, url} can be written under the item element as in Example 1, or without the item element as in Example 2.
* We recommend using one listItem per page.
* ListItems with small numbers are not used.
* Please be careful to avoid duplication between elements.
#### Image Guidelines
* Please use the original image, not a thumbnail, etc.
* Please avoid duplication between images.
* Please use an image that well represents the item. Avoid using logos, default images, or broken images.

#### Types and Properties
  [ListItem](https://schema.org/ListItem) defined by schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| name | Not required | Please enter the name of each item.  |
| image | **essential** | This is an image representing the item.   Use in [ImageObject](https://schema.org/ImageObject) or [URL](https://schema.org/URL) format. |
| url | Not required | Please enter the relevant URL for the item.  Please use the [URL](https://schema.org/URL) format and enter an absolute path, not a relative path or shortened URL. |
| item | Not required | When creating an item element, the image is required, and other elements are optional.   It can be written in all types under [Thing](https://schema.org/Thing). |
| position | Not required | List number.  Please write in [Integer](https://schema.org/Integer) format. |

* Example 1 implemented in JSON-LD format (write {name, image, url} under the item element)
```
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "ItemList",
  "itemListElement":[
    {
      "@type": "ListItem",
      "item": {
        "@type": "Organization",
        "name": "라인",
        "image": "https://example.com/photos/listitem-1.jpg",
        "url": "https://example.com/listitem-url-1"
      },
      "position": "1"
    },
    {
      "@type": "ListItem",
      "item": {
        "@type": "Organization",
        "name": "네이버 랩스",
        "image": "https://example.com/photos/listitem-2.jpg",
        "url": "https://example.com/listitem-url-2"
      },
      "position": "2"
    },
    {
      "@type": "ListItem",
      "item": {
        "@type": "Organization",
        "name": "네이버 클라우드",
        "image": "https://example.com/photos/listitem-3.jpg",
        "url": "https://example.com/listitem-url-3"
      },
      "position": "3"
    },
    {
      "@type": "ListItem",
      "item": {
        "@type": "Organization",
        "name": "네이버 웹툰",
        "image": "https://example.com/photos/listitem-4.jpg",
        "url": "https://example.com/listitem-url-4"
      },
      "position": "4"
    },
    {
      "@type": "ListItem",
      "item": {
        "@type": "Organization",
        "name": "스노우",
        "image": "https://example.com/photos/listitem-5.jpg",
        "url": "https://example.com/listitem-url-5"
      },
      "position": "5"
    },
    {
      "@type": "ListItem",
      "item": {
        "@type": "Organization",
        "name": "네이버 파이낸셜",
        "image": "https://example.com/photos/listitem-6.jpg",
        "url": "https://example.com/listitem-url-6"
      },
      "position": "6"
    }
  ]
}
</script>
```
* Example 2 implemented in JSON-LD format (written without item element)
```
<script type="application/ld+json">
{
  "@context":"http://schema.org",
  "@type":"ItemList",
  "itemListElement":[
    {
      "@type": "ListItem",
      "name": "라인",
      "image": "https://example.com/photos/listitem-1.jpg",
      "url": "https://example.com/listitem-url-1",
      "position": "1"
    },
    {
      "@type": "ListItem",
      "name": "네이버 랩스",
      "image": "https://example.com/photos/listitem-2.jpg",
      "url": "https://example.com/listitem-url-2",
      "position": "2"
    },
    {
      "@type": "ListItem",
      "name": "네이버 클라우드",
      "image": "https://example.com/photos/listitem-3.jpg",
      "url": "https://example.com/listitem-url-3",
      "position": "3"
    },
    {
      "@type": "ListItem",
      "name": "네이버 웹툰",
      "image": "https://example.com/photos/listitem-4.jpg",
      "url": "https://example.com/listitem-url-4",
      "position": "4"
    },
    {
      "@type": "ListItem",
      "name": "스노우",
      "image": "https://example.com/photos/listitem-5.jpg",
      "url": "https://example.com/listitem-url-5",
      "position": "5"
    },
    {
      "@type": "ListItem",
      "name": "네이버 파이낸셜",
      "image": "https://example.com/photos/listitem-6.jpg",
      "url": "https://example.com/listitem-url-6",
      "position": "6"
    }
  ]
}
</script>
```
* Example 1 implemented in Microdata format (write {name, image, url} under the item element)
```html
<ol itemscope itemtype="https://schema.org/ItemList">
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <span itemprop="item" itemscope itemtype="https://schema.org/Organization">
      <span itemprop="name">라인</span>
      <img itemprop="image" src="https://example.com/photos/listitem-1.jpg"/>
      <link itemprop="url" href="https://example.com/listitem-url-1" />
    </span>
    <meta itemprop="position" content="1" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <a itemprop="item" itemscope itemtype="https://schema.org/Organization">
      <span itemprop="name">네이버 랩스</span>
      <img itemprop="image" src="https://example.com/photos/listitem-2.jpg"/>
      <link itemprop="url" href="https://example.com/listitem-url-2" />
    </a>
    <meta itemprop="position" content="2" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <a itemprop="item" itemscope itemtype="https://schema.org/Organization">
      <span itemprop="name">네이버 클라우드</span>
      <img itemprop="image" src="https://example.com/photos/listitem-3.jpg"/>
      <link itemprop="url" href="https://example.com/listitem-url-3" />
    </a>
    <meta itemprop="position" content="3" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <a itemprop="item" itemscope itemtype="https://schema.org/Organization">
      <span itemprop="name">네이버 웹툰</span>
      <img itemprop="image" src="https://example.com/photos/listitem-4.jpg"/>
      <link itemprop="url" href="https://example.com/listitem-url-4" />
    </a>
    <meta itemprop="position" content="4" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <a itemprop="item" itemscope itemtype="https://schema.org/Organization">
      <span itemprop="name">스노우</span>
      <img itemprop="image" src="https://example.com/photos/listitem-5.jpg"/>
      <link itemprop="url" href="https://example.com/listitem-url-5" />
    </a>
    <meta itemprop="position" content="5" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <a itemprop="item" itemscope itemtype="https://schema.org/Organization">
      <span itemprop="name">네이버 파이낸셜</span>
      <img itemprop="image" src="https://example.com/photos/listitem-6.jpg"/>
      <link itemprop="url" href="https://example.com/listitem-url-6" />
    </a>
    <meta itemprop="position" content="6" />
  </li>
</ol>
```
* Example 2 implemented in Microdata format (written without item element)
```html
<ol itemscope itemtype="https://schema.org/ItemList">
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <span itemprop="name">라인</span>
    <img itemprop="image" src="https://example.com/photos/listitem-1.jpg"/>
    <link itemprop="url" href="https://example.com/listitem-url-1" />
    <meta itemprop="position" content="1" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <span itemprop="name">네이버 랩스</span>
    <img itemprop="image" src="https://example.com/photos/listitem-2.jpg"/>
    <link itemprop="url" href="https://example.com/listitem-url-2" />
    <meta itemprop="position" content="2" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <span itemprop="name">네이버 클라우드</span>
    <img itemprop="image" src="https://example.com/photos/listitem-3.jpg"/>
    <link itemprop="url" href="https://example.com/listitem-url-3" />
    <meta itemprop="position" content="3" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <span itemprop="name">네이버 웹툰</span>
    <img itemprop="image" src="https://example.com/photos/listitem-4.jpg"/>
    <link itemprop="url" href="https://example.com/listitem-url-4" />
    <meta itemprop="position" content="4" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <span itemprop="name">스노우</span>
    <img itemprop="image" src="https://example.com/photos/listitem-5.jpg"/>
    <link itemprop="url" href="https://example.com/listitem-url-5" />
    <meta itemprop="position" content="5" />
  </li>
  <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
    <span itemprop="name">네이버 파이낸셜</span>
    <img itemprop="image" src="https://example.com/photos/listitem-6.jpg"/>
    <link itemprop="url" href="https://example.com/listitem-url-6" />
    <meta itemprop="position" content="6" />
  </li>
</ol>
```
