# Favicon

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/markup-favicon)

[Favicon](https://terms.naver.com/entry.nhn?docId=864878&cid=50371&categoryId=50371) is an icon representing a website or web page displayed in the address bar of an Internet web browser.

![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfODUg/MDAxNzkyMDUwMDc5ODMw.od0xRJtEqWH9eMp5HXsvUeBMeGvkD5TOJxzPBdTtyj4g.dKeiUGQYWAd1zPchzzK2brR5ubUASUwN2c62R9b4pUcg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%ED%8C%8C%EB%B9%84%EC%BD%98.png)

If you follow the guidelines below, your favicon may be displayed in Naver search results.

### STEP 1. Check favicon size, file format, and basic rules

#### basic rules
1. The Naver crawler must be able to collect the favicon.  Refer to [Setting up robots.txt](../seo-basics/configuring-robots-txt.md) guide
2. I don't change my favicon URL often.
If the favicon URL and image change, update may be delayed and the favicon image in search results may be inconsistent.
Even when replacing images at the same address, re-collection is necessary, so it may take time to reflect depending on the situation.
3. Use unique images that represent your website.
4. We do not use pornography or images that make users feel disgusted.

#### Favicon size
* It must be square with equal width and height and at least 16px tall. (e.g. 30 x 30px, 48 x 48px)
* When exposed in search results, the size of the obtained favicon is resized and displayed to an appropriate size on the screen. Therefore, we recommend a size of 32px or larger for beautiful display in various environments.

#### Favicon file format
It supports [file format](https://en.wikipedia.org/wiki/Favicon#File_format_support) as shown below.

| ICO | PNG | GIF | animated GIFs | JPEG | APNG | SVG |
| -- | -- | -- | -- | -- | -- | -- |
| O | O | O | O | O | O |  O |

* You can set the background color to transparent.

### STEP 2. Favicon markup


Utilize the `<link>` tag within the `<head>` tag in the HTML document.


The href where the favicon is located must use an absolute path, not a relative path.

```
<head>
<link rel="shortcut icon" href="http://www.mysite.com/favicon.ico">
</head>
```

You can use one of the rel attributes below.

```
* shortcut icon
* icon
* apple-touch-icon
* apple-touch-icon-precomposed
```

### Q. If there are multiple favicon markups on the page, which one is reflected?
If there are multiple favicon markups within a web page, the favicon used for search exposure is processed by determining priority based on the rules below.

* Processing is based on the order below of the rel attribute described in the markup and the site's default favicon.

1. shortcut icon
1. icon
1. default icon (host url + /favicon.ico)
1. apple-touch-icon
1. apple-touch-icon-precomposed

* Please ensure that there is only one identical rel attribute value. If there are multiple, it may cause the image not to be reflected.


### Q. I set/changed the favicon, but it is not reflected.
* Please re-check whether the favicon meets the above standards.
* Please check whether the favicon file is in a collectible path or restricted by robots.txt, etc.
* Collection of favicons also requires a visit by a Naver robot separately from document collection. The robot's visit may take some time because it may visit other pages or resources.
* If you update the favicon with the same file name, the update may be delayed depending on the cache, etc.
