# Site status

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/site-summary)

The site status information provided by Webmaster Tools is a report that provides improvements identified during the process of Naver crawler collecting site content.
Site crawling and indexing are processed normally, but we are providing guidance on areas that would like to be improved for better site quality.  `(사이트 상태는 1~2일 주기로 업데이트됩니다.)`
![image](https://searchadvisor-phinf.pstatic.net/MjAyMjEwMjVfMTU1/MDAxNjY2Njg1ODAxOTAw.b0TXX0Ung_bkrWZ8EfsJmhQwi2A0H3eG_b_K4-TlgVcg.y1SRSFvI9655GtuJtffYya8cLucBiq9Fl38tcbBjibsg.PNG/report-summary-status-3.PNG)

### security certificate
Check the validity of the security certificate provided by the site, including whether it is registered correctly, whether it is issued by a trustworthy certification authority, and whether the certificate has not expired.

situation | message | explanation
---|---|---
normal | The security certificate is normal. | no problem
Confirmation required | Security certificate verification is required. | When collecting some documents, check for invalid certificates
Confirmation required | Please register as an HTTPS site with Search Advisor. | A security certificate exists, but the site is registered with a URL other than HTTPS.
problem | A security certificate issue has been detected. | Check for certificate errors in all recently collected documents
Not applied| You must apply the security certificate after receiving it. | Security certificate not applied
Confirming| Confirming. | -


### HTTPS redirection
If you operate both HTTP and HTTPS sites after applying the security certificate, the redirection status will be checked and you will be notified.
Naver Robot collects data by prioritizing HTTPS among HTTP and HTTPS. If you run a site using both protocols without redirection, you may be disadvantaged due to duplicate collection and security issues.
If you have applied a security certificate, please operate as an HTTPS site.
Please check the HTTPS redirection section according to the report results below.

situation | message | explanation
---|---|---
normal | It's normal. | When accessing an HTTP site, you are redirected to an HTTPS site.
normal | Naver Search recommends providing pages via HTTPS. |  Both HTTP and HTTPS sites are connected, but when connecting via HTTP, you are not redirected to HTTPS.
Confirmation required | Naver Search recommends providing pages via HTTPS.  | When connecting via HTTPS, you are redirected to an HTTP site or the HTTPS connection is unstable.
Confirming| Confirming. | -




### sitemap
We will check site map registration and status and provide guidance. Please check the site map according to the report results below.

situation | message | explanation
---|---|---
normal | Sitemap has been registered. | If registered properly through Search Advisor
normal | The sitemap has been confirmed in robotx.txt. | If you are not registered as a search advisor, but the sitemap is confirmed in robots.txt
Not registered | Please submit your sitemap | If you are not registered as a search advisor or not confirmed in robots.txt
Confirmation required | Sitemap not found. | If you registered through Search Advisor, but cannot access the site map (not 200 ok)
Confirming | Confirming. | -
