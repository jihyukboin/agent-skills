# Verifying Naver's crawler

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-basic-firewall)

The program or app that visits the web page specifies its own name in [User-Agent](https://www.w3.org/WAI/UA/work/wiki/Definition_of_User_Agent). Not only regular web browser software but also crawlers have their own User-Agent names.

Many websites operate [fire door](https://terms.naver.com/entry.nhn?docId=1179934&cid=40942&categoryId=32853) to prevent some malicious access. If your site is not exposed in searches or the information does not change, you should check whether robots working for this purpose are blocked from accessing the site due to firewall restrictions such as the User-Agent name or IP address.

In order to distinguish whether a robot is operated by Naver, there are two ways: using User-Agent to distinguish it, and confirming it by IP through reverse DNS lookup.

### Check with User-Agent name

The crawler that collects web documents for the general Naver search service is called Yeti.
Use the User-Agent name below. Detailed versions, etc. may change without prior notice.
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko; compatible; Yeti/1.1; +https://naver.me/spd) Chrome/W.X.Y.Z Safari/537.36
```

or

```
Mozilla/5.0 (compatible; Yeti/1.1; +https://naver.me/spd)
```


In addition, for special purposes, professional robots such as a robot (UA: Ads-Naver) that collects additional information for effective advertising exposure on advertiser pages and a robot (UA: Blueno) that collects previews when inserting links in blog editors, etc. may be active.
[About advertising web collection robots](https://ads.naver.com/help/faq/994)
[About the summary information collection robot](https://help.naver.com/service/5626/contents/19008?lang=ko)



### Check with IP information
The robot's access can be identified using the User-Agent information in the HTTP header explained earlier. However, if you are not sure whether the access is from the Naver server based on this information alone, you can check using the following method.

##### Verification via reverse DNS lookup

1. Perform a reverse DNS lookup for the IP address of the accessor in the web server log or firewall access record and check whether the searched domain ends with .naver.com.

2. Perform a DNS lookup for the domain obtained above to check if it is the same as the original IP address.

```
* 예시 (리눅스/MacOS)
$ host 125.209.235.169
169.235.209.125.in-addr.arpa domain name pointer crawl.125-209-235-169.web.naver.com.

$ host crawl.125-209-235-169.web.naver.com
crawl.125-209-235-169.web.naver.com has address 125.209.235.169
```
```
* 예시 (Windows, 윈도우키 + R 입력 후 cmd 실행)
C:\Users> nslookup 125.209.235.169
Server: 168.126.63.1
Address: 168.126.63.1

Name: crawl.125-209-235-169.web.naver.com
Address: 125.209.235.169

C:\Users> nslookup crawl.125-209-235-169.web.naver.com
Server: 168.126.63.1
Address: 168.126.63.1

Name: crawl.125-209-235-169.web.naver.com
Address: 125.209.235.169
```

##### Verification through list comparison

You can attempt to identify the IP address you want to identify in an automated manner by comparing it with the [IP range list](https://searchadvisor.naver.com/doc/naverbot.json) (JSON / [CIDR](https://wikipedia.org/wiki/Classless_Inter-Domain_Routing) format) used by the Naver crawler.
However, the contents of the list may change without notice.
