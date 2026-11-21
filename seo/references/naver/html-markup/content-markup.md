# Content markup

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/markup-content)

### page title
Use the \<title\> tag within the \<head\> tag of the HTML document.

```
<head>
<title>페이지 제목</title>
</head>
```

#### ◆ TIP for writing page titles!
The title tag on the site's main page must be entered with a brand name that best expresses the personality of the site. It is recommended to use brand keywords that fit the purpose of establishing the site, and it is recommended to use proper nouns such as business name, service name, and product name. Additionally, if you change the title frequently just for search exposure, or if the title is too long and users cannot easily understand the site, you may be penalized for search exposure.

The title tag of each page must contain a phrase that clearly describes the topic of the page's content. There is no separate character limit, but we recommend that you limit the length of the title to a level that can be expressed in search results. Excessively long titles can hinder usability for search users. Please note that keywords that are repeated more than twice, spam keywords, keywords or promotional phrases that are not related to the content, etc. may be penalized in search exposure.

Don't give every page on your site the same title. A unique title that matches the content of your page increases the likelihood that searchers will find your content.

The title used for search exposure is determined by automatically extracting the most appropriate information from various information such as the page and anchor, including the content specified by the search engine in this tag and the Open Graph tag below.

### Page Description
Use the \<meta\> tag within the \<head\> tag of the HTML document.

```
<head>
<meta name="description" content="페이지 설명">
</head>
```

#### ◆ TIP for writing page descriptions!

The page's description tag is a brief description of the page's content, which can be a short paragraph of 1-2 sentences. However, if there are keywords that are repeated more than twice, spam keywords, or keywords that are not related to the site, you may be penalized for search exposure. Additionally, if the content of the description tag on the site's main page is changed frequently just for search exposure or is excessively long, making it difficult for users to easily understand the site, this may also be subject to disadvantages.

In some cases, the entire content of the page is copied and pasted, the title is the same, all tags on other pages on the site are the same, or only keywords are listed. In this case, you may be penalized for search exposure, so please narrow down and include only the necessary phrases that fit the content.

The descriptions and snippets that are actually displayed in the search results are created by the search engine automatically extracting the most appropriate information from various types of information, including the above tags and text within the body, based on the results of the user's search keywords and intent analysis.

### open graph

Open Graph tags are information that is prioritized when a site is shared on social media. However, the Naver crawler may also use the information simultaneously for page analysis and exposure, so it is recommended that you fill it out together if possible. In particular, Open Graph can include representative images as well as the site's title and description. For full format details, please refer to [http://ogp.me](https://ogp.me/).

For markup, use the \<meta\> tag within the \<head\> tag of the HTML document.

```
<head>
<meta property="og:type" content="website">
<meta property="og:title" content="페이지 제목">
<meta property="og:description" content="페이지 설명">
<meta property="og:image" content="http://www.mysite.com/myimage.jpg">
<meta property="og:url" content="http://www.mysite.com">
</head>
```


#### open graph image
Open Graph Image (og:image) can be used as an image thumbnail representing a site or page within Naver search results. We recommend that you check the following items so that the image you entered can be used effectively.

* Image size must be greater than 150x150.
* Image file size must be 5,000 bytes or more.
* The image width:height ratio must not exceed 3:1.
* Please make sure that it is a unique image that can represent each document. In the case of images that appear repeatedly on different pages, images such as logos that are repeated throughout the site, and promotional banner images, search engines may not use them because they may not be viewed as representative images of individual pages or may confuse users when displayed in search results.

### social media
Use the \<meta\> tag within the \<head\> tag of the HTML document.

```
<head>
...
<meta property="og:type" content="website">
<meta property="og:title" content="페이지 제목">
<meta property="og:description" content="페이지 설명">
<meta property="og:image" content="http://www.mysite.com/article/article1_featured_image.jpg">
<meta property="og:url" content="http://www.mysite.com/article/article1.html">
...
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="페이지 제목">
<meta name="twitter:description" content="페이지 설명">
<meta name="twitter:image" content="http://www.mysite.com/article/article1.html">
<meta name="twitter:domain" content="사이트 명">
...
</head>
```

Please include various additional information provided by social media in the page meta information.
By determining what content is shared not only in searches but also on social media, you can increase page visits.
