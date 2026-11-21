# Removing pages from web search

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/faq-serpremove)

### Site exclusion policy from Naver search

Naver can only remove a product from Naver search results in case of policy violation such as violation of law or copyright violation.  If the site is accessed normally, please understand that Naver cannot arbitrarily delete it.

Blocking or deleting a web page usually has to be done through the administrator or owner who controls the website.  The reason why you must request deletion from the owner who has the authority to delete the content is because even if it is deleted from search results, the content itself is not deleted, so there is a high possibility that related pages will still remain and be displayed in site link URLs, social media, and other search engines.

If you have a court order to delete a post due to defamation, etc., which may be legal grounds, please contact [customer service center](https://help.naver.com/support/alias/webmastertool/webmastertool_19.naver).

### Q. I would like to exclude a site I own from Naver search results.

If you do not want to close your site, but rather exclude it from Naver searches, you must perform one or more of the following actions.

#### 1. Insert the NOINDEX meta tag into the web page.

`<head><meta name="robots" content="noindex"></head>`

Although it is inconvenient to specify it in all documents, adding the above meta tag
The robot will know that you do not want the document to appear in search results.

However, if the page simply redirects to another URL, this setting alone may not exclude the URL.
In this case, it is necessary to additionally set robots.txt, or set noindex meta or completely delete the redirect target pages.

#### 2. Completely delete the web page or return an error page
If it is determined that the web page is no longer needed, the web server returns an appropriate [HTTP response code](../seo-basics/http-protocol.md), such as 403 (Forbidden) or 404 (Not Found).
Similarly, it is also possible to redirect to an error page or notify that the page requires authentication. However, depending on the page configuration, the robot may mistake it for a normal response, so caution is required.

In particular, if you use techniques such as using javascript or CSS to cover the screen while leaving the content as is, or to bring up an error message or login, etc.
This information may not be recognized properly when the robot interprets the page.


#### `주의: robots.txt를 먼저 설정하거나 서버의 네트워크를 먼저 정지하거나 블럭하지 마세요`
robots.txt is a setting that blocks further access by crawlers, regardless of whether the document or site has disappeared from the Internet.

In other words, in order to check whether the site or document has been deleted, the robot must visit the site and check.
If robots.txt, etc. is set in front, even access to check it is blocked, so the desired operation may not work.

In addition, if the server's network is unconditionally stopped or blocked at the network level, as above, the robot cannot determine whether the server is still operating or whether it is a temporary error.
It may not be possible to reflect what you want.

If you do not want to be exposed in searches in the future, we recommend that you first delete it according to the guide, confirm that all related pages have disappeared from searches, and then set robots.txt, etc.


### Q. I would like to exclude only certain pages of the site I own from search results.

If you want to exclude only specific pages from search results, insert the tag below into the `<head> ` tag of the page you want to exclude.

`<head><meta name="robots" content="noindex"></head>`

When the Naver crawler revisits the page, it recognizes the tag and excludes it from the index.
If you want to visit the crawler a little faster, you can request collection using Webmaster Tools.

### Q. I would like to exclude inaccessible pages from Naver search results.

If the page has been deleted, please wait a moment for the deleted content to be reflected in search results. After a certain period of time, it goes through an update process and is automatically excluded from search results.

If the site has been verified as owned by Webmaster Tools, you can request page exclusion using Webmaster Tools. After logging in to Webmaster Tools, enter the sub-address through the **Request > Exclude web page search** menu and press the OK button.

However, please be aware that pages that do not delete the original or restrict search collection may be re-exposed in search results!

### Q. The website operator is unable to contact me. How do I exclude sites that are no longer in operation from Naver search results?

If the website operator (webmaster) is unable to cooperate, you can contact the site hosting company, etc.
For most site hosting companies, you can find information such as the hosting company's contact information by searching the site URL in a place where you can find whois information, such as [https://WhoisSearch.Korea/](https://후이즈검색.한국/).
