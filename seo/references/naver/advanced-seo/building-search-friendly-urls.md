# Building search-friendly URLs

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/seo-advanced-url)

Plan the URL structure when you first build your site. Choose a structure that reflects how you organize content and is easy to understand.

For example, consider these two URLs for a creator guide:

- Harder to interpret: `https://www.mysite.com/1001125/1079/action.do?tab=guide&method=selectPage&menu_id=EMWPCnslWebInqL`
- Easier for users and crawlers: `https://www.mysite.com/guide/creator`

## URL structure

A [URL](https://terms.naver.com/entry.nhn?docId=3571733&cid=59088&categoryId=59096) identifies the location of a network resource and commonly serves as the address of a web page.

Example: `https://search.naver.com/search.naver?query=naver&page=2&where=web#section`

- **Protocol** (`https`). Naver recommends the more secure [HTTPS protocol](https://terms.naver.com/entry.nhn?docId=3436086&cid=42346&categoryId=42346).
- **Host** (`search.naver.com`). The server that delivers the content. Choose a readable hostname that reflects the site.
- **Domain name** (`.naver.com`). Naver recommends owning an independent domain whose name matches the content.
- **Path and filename** (`/search.naver`). The location of the resource on the web server. Case sensitivity depends on the server. Lowercase is customary.
- **Parameters** (`q=search`, `sort=desc`). Additional information sent to the server as key-value pairs. Use `&` between parameters and `=` between a key and its value.
- **Fragment** (`section`). Identifies a specific part of the same page, such as the [history section of Wikipedia's K-pop article](https://ko.wikipedia.org/wiki/K-pop#역사).

## Search-friendly URLs

- Use a familiar top-level domain, such as `.com`, `.net`, `.co.kr`, `.kr`, or `.io`.
- Choose your own domain that reflects the site. For example, use `www.mysite.com` in place of a default hosting domain such as `mysite.web-hosting.com`.
- Use URLs that both visitors and search engines can understand. Minimize URL parameters. Prefer `https://www.mysite.com/guide/seo-basic-intro` to `https://www.mysite.com/guide.php?page=seo-basic-intro&sort=default`.
- Give distinct content its own URL because the search engine disregards fragments. Use `https://www.mysite.com/start` and `https://www.mysite.com/diagnose`. Avoid `https://www.mysite.com/?tab=guide#start` and `https://www.mysite.com/?tab=guide#diagnose`.
- The search engine also disregards hashbangs (`#!`). For `https://www.mysite.com/path/to/#!/some-ajax-state`, it recognizes only `https://www.mysite.com/path/to/`.

## Search-friendly links

Naver's crawler extracts links from web pages and treats their URLs as candidates for crawling. Mark up links so the crawler can identify their destinations.

When a page relies solely on JavaScript for links, a crawler may be unable to determine the destination or discover other useful information there. Use standard link URLs to help Naver discover your internal pages.

- `<a href="http://www.mysite.com">Link</a>` gives the crawler an explicit destination.
- `<span onClick="javascript:goto(A)">Link</span>` provides only a JavaScript function. The crawler cannot determine the exact URL.

Dynamically changing links can also be difficult to interpret. Use static link markup where possible, particularly when:

- The destination varies by session or cookie.
- The destination changes depending on whether the visitor opens the page directly or arrives through another page.
