# Site registration and ownership verification

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/faq-start-register)

Naver web search reflects and displays site information automatically collected by a web collection robot. Therefore, there is no search registration process.  It is a priority to refer to the [Search Engine Optimization](../seo-basics/the-purpose-of-search-engine-optimization.md) guide and take steps to ensure that crawlers can collect websites well.

Even if you do not register your site in Naver Webmaster Tools, your site and web documents will be reflected in Naver search results. However, if you register your site in Naver Webmaster Tools and proceed with the [Confirmation of ownership](https://help.naver.com/support/contents/contents.help?serviceNo=14882&categoryNo=15032) procedure, you can identify the collection, indexing, and exposure information of content within the site through reports. After verification of ownership, you can use the report in Webmaster Tools to check the status of your site's search integration, which can be of great help to site operation.

Ownership verification does not support JavaScript execution, so to check markup, enter view-source:site_URL in the URL input box of a recent web browser or use View Page Source.

Things to keep in mind when verifying meta tags and HTML for ownership verification in Search Advisor are as follows.

* When verifying meta tags for ownership verification in Search Advisor, browser-side redirection using **JavaScript, meta refresh, and cookie** is not supported. If a redirect is necessary, please process it as [http redirect (301, 302)](../seo-basics/http-protocol.md), which is processed on the web server.
```
# another.html 에 존재하는 소유확인용 메타태그 확인 불가
<head>
...
<meta http-equiv="refresh" content="0;url=another.html">
...
</head>
```

```
# another.html 에 존재하는 소유확인용 메타태그 확인 불가
<html>
...
<script lang=javascript>
window.location.href = "./another.html"
</script>
...
</html>
```

```
# 소유확인용 메타태그 확인 불가
<html>
...
<script lang=javascript>
document.cookie = 'sample_key=sample_value'
window.location.reload();
</script>
...
</html>
```

* If meta tag information for ownership verification exists within the html frame tag, it is excluded from verification. Please enter it within the html head tag, not the frame tag.
```
...
<FRAME SRC="http://another.domain.com">
...
```

* If meta tag information for ownership verification exists within the html body tag, it is excluded from verification. Please enter it within the html head tag.
```
# 소유확인용 메타태그가 body 태그내에 존재하므로 확인 불가
<html>
<head>
<title>예제</title>
</head>
<body>
<meta name="naver-site-verification" content="...."/>
</body>
</html>
```
