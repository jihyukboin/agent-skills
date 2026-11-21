# Moving a web page

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-basic-redirect)

There are some things to be careful about when redirecting (moving) a web page to a different address for reasons such as changing the site.

#### Please refrain from redirecting using JavaScript.
When using the JavaScript format when redirecting sites and pages, it is generally difficult for crawlers to understand, so it is difficult to understand which URL the link is redirected to.

In addition, pages that hide redirect information are often found in spam documents, so even though they are high-quality pages, they may be undervalued as unnecessarily low in importance in the spam document processing process.

Therefore, not using JavaScript functions when processing URL links or redirects helps provide correct information to crawlers.

If you want to notify visitors that the address is being redirected, you can use meta refresh, and Naver's crawler recognizes meta refresh. However, the HTML 4.01 standard recommends not using meta refresh, so please use HTTP redirect if possible.

* Example of incorrect redirect usage
```
var timerld = setTimeout("move()", 500);
function move() {
  location.href = "http://new.site.com/";
  timerld = 0;
}
```
* Example of using meta refresh
```
<meta http-equiv="refresh" content="10;url=http://new.site.com">
```

#### When changing a site or page, please use a redirect in the 301 Permanently Moved format.
If you change the URL of a site or internal page, crawlers may mistakenly believe that the information is new and different from the existing site or internal page. Additionally, the existing good search information and search user preference information may not be used in the subsequent redundant information processing process.

When changing the URL, informing the crawler of the existing URL so that it can utilize the existing information is very helpful for search exposure.
To let us know, please respond from the server using a redirect in the form of 301 permanently moved according to http regulations.
* Redirect the entire old host to the new host's top page (apache web server)
```
Redirect 301 / http://new.site.com
혹은
Redirect permanent http://new.site.com
```
* redirect example.com/* to www.example.com/* (apache web server)
```
RewriteEngine On
RewriteCond %{HTTP_HOST} example.com
RewriteRule ^([^/]*})$ http://www.example.com [R=301,L]
```

#### In case of site failure or temporary page change, please use a redirect in the 302 Temporarily Moved format.
If the site has a temporary outage or the page changes briefly, crawlers may mistakenly believe that the page has been deleted if they do not receive a response regarding the site and its internal pages. If we are not aware of temporary page changes, we may determine that the information has changed to other information and delete the existing information.

If you wish to maintain the information of the original page collected by the existing unwanted crawler, please respond from the server using a 302 redirect in accordance with http regulations when there is a temporary problem on the site or the page is temporarily changed.

* Redirect to page under construction (apache web server)
```
Redirect / /under_const.html
혹은
Redirect temp / /under_const.html
```

#### Minimize the number of consecutive redirects.
This refers to a case where a page redirects continuously, and the number of redirections exceeds the range set in the crawler. It is recommended that the number of consecutive redirections not exceed a maximum of 5. In addition, there are program problems that cause redirects to repeat themselves infinitely, but even in this case, the crawler does not collect them.

We ask that you minimize the use of continuous redirects as much as possible. Since redirection problems have limitations in being visible in the browser you use, we recommend using the developer tools provided by your browser or working with the site's technical staff to resolve the issue.

#### The moving process and final landing URL must be a normal page that can be collected.
In some cases, the final landing URL that is redirected to is a page that does not exist or is set to prevent crawlers from accessing it. If the URL address containing normal content has changed due to reasons such as site reorganization, it is necessary to check whether the URL is properly redirected before and after the change.

Especially in the case of multiple redirections, all addresses in the connection process must be able to be collected. Please note that if there is a mistake in the robots.txt settings and URLs that cannot be collected are mixed in, collection may not occur even if the first and final URLs are collectable.

#### If you want to block Naver crawlers for a while due to site performance or internal policy issues, use traffic restrictions in Webmaster Tools.
If you need to temporarily block access from Naver crawlers, we recommend setting the traffic limit to the minimum in the collection settings of Webmaster Tools. There is also a way to block crawlers with robots.txt, but in this case, documents on the site collected during that period may be excluded from Naver searches.

#### It may take time to reflect redirection changes.
If you set up a new redirect or change it due to a site reorganization, etc., it may take time for the search results to be reflected.

After collecting individual documents, the crawler compiles the information collected through a separate process to analyze and update the redirect or site structure, so it may take time to update the information during this process. Therefore, if the homepage address, etc. changes due to a site reorganization, etc., it is recommended that, if possible, set a redirect to URLs that were exposed in existing searches for a while to ensure that services can be provided regardless of search engine updates.
