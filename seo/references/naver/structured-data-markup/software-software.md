# Software (Software)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-software)

### Software

* Displays software information.

![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMiAg/MDAxNzkyMDQ5NTM5Njc5.pNGvbA73t7HaWIkUd2-1lVAURyuSTiA8Gj8RPVeSskwg.a1t6Ge-MUNhdU8Vgih8LpFIVnVPnWZGjUwm95LwEk6Mg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.


### Software markup

#### basic guidelines
* This is information about software running on PC/mobile/tablet, etc.

#### Types and Properties
  [Software Application](https://schema.org/SoftwareApplication) defined by Schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| name |  **essential**  | Please enter the software name. |
| applicationCategory |  **essential**  | Please enter a software category. |
| operatingSystem | Not required | Please enter the operating system you support. (Example: Android, iOS) Please enter them one by one. If you have version information, please enter it as well. |
| url | Not required | Please enter the software webpage or download URL. Please use the URL format and enter an absolute path, not a relative path or shortened URL. |
| screenshot | Not required | This is a screenshot. Used in ImageObject or URL format. |
| description | Not required | This is a description of the software. Please write content-oriented so that it is not too long. |

* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "네이버 유틸리티",
  "applicationCategory": "유틸리티",
  "operatingSystem": [
    "iOS",
    "Android"
  ],
  "url": "https://example.com/software_url",
  "screenshot": [
    {
      "@type": "ImageObject",
      "url": "https://example.com/photos/software_1.jpg",
       "width": "700",
      "height": "500"
    },
    {
      "@type": "ImageObject",
      "url": "https://example.com/photos/software_2.jpg",
       "width": "700",
      "height": "500"
    }
  ],
  "description": "네이버 유틸리티 애플리케이션입니다."
}
</script>

```

* Example implemented in Microdata format
```html
<div itemscope itemtype="https://schema.org/Movie">
 <span itemprop="name">네이버 유틸리티</span>
 <span itemprop="applicationCategory">유틸리티</span>
 <span itemprop="operatingSystem">iOS</span>
 <span itemprop="operatingSystem">Android</span>
 <link itemprop="url" href="https://example.com/software_url" />
 <img itemprop="screenshot" src="https://example.com/photos/software_1.jpg"/>
 <img itemprop="screenshot" src="https://example.com/photos/software_2.jpg"/>
 <span itemprop="description">네이버 유틸리티 애플리케이션입니다.</span>
</div>
```
