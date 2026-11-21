# Mobile usability

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/markup-mobile)

#### responsive web
Use the \<meta\> tag within the \<head\> tag of the HTML document.

```
<head>
<meta name="viewport" content="width=device-width">
</head>
```
Responsive web is a technique where the web browser automatically adjusts the width of a web document to match the device screen size. Responsive web helps users consume your web content more easily in a mobile environment that supports various sizes without having to zoom in/out the page.

#### Separate mobile URL provided
Use the \<link\> tag within the \<head\> tag of the HTML document.

If your site has a separate mobile site that corresponds to the desktop site for the same content, we recommend explicitly specifying the URL of the desktop site that corresponds 1:1 to the mobile site page. This task informs Naver's crawler so that content is not processed redundantly when it visits your desktop and mobile sites. Additionally, please register both the desktop and mobile sites in Webmaster Tools so that Naver crawlers are aware of the existence of the mobile site.

For example, assuming that you have http://www.mysite.com as a desktop site and http://m.mysite.com as a corresponding mobile site, it is recommended to specify the desktop URL on the page within http://m.mysite.com as shown below.

Main page of mobile site - example) http://m.mysite.com/

```
<head>
<link rel="canonical" href="http://www.mysite.com/">
</head>
```

Individual web pages on mobile site - e.g. http://m.mysite.com/article/article1.html

```
<head>
<link rel="canonical" href="http://www.mysite.com/article/article1.html">
</head>
```

#### Automatic redirect processing according to the site visitor’s web browser environment
When accessing your desktop site from a mobile device, please redirect to the mobile site. Similarly, when accessing a mobile site from a desktop, you should also consider redirecting to the desktop site. Since every web browser has its own name (User Agent Name), you can technically tell whether a site visitor's web browser is mobile or desktop.

For example, when accessing http://m.mysite.com/ from a desktop, it is redirected to http://www.mysite.com, and when accessing http://www.mysite.com from a mobile device, it is redirected to http://m.mysite.com.

Please use HTTP redirect, not JavaScript, when redirecting according to the user's web browser environment. Naver crawler detects HTTP redirects, but may not detect JavaScript redirects in some cases. If it is difficult to use HTTP redirect due to technical issues, we recommend using JavaScript redirect but leaving the HTML body blank.
