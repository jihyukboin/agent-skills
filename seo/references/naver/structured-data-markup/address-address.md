# Address (Address)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-address)

###  Address

* This is the address information displayed in search results.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMjQx/MDAxNzkyMDQxMzY1MDEy.M_mbM4qqKVPaJF455ZeQwApKitVj9U0O3gWkUkSyo_kg.vRIgB2WK7STZspy7LTZNwCrdsP37XaUgqnRM7SFa6a0g.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%A3%BC%EC%86%8C_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.

### Address markup

* basic guidelines
    * Please be careful not to use the same site common address on multiple pages.
    * Please enter the appropriate information for each element without duplication.
    * Please be as detailed and clear as possible.
* Types and Properties
  [PostalAdress](https://schema.org/PostalAddress) defined by schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| postalCode | Not required | Please enter your zip code using numbers or hyphens (-).  |
| addressRegion | Not required | Please enter the largest region name among your addresses. |
| addressLocality | Not required | Region Please enter the sub-region. |
| streetAddress | **essential** | Please enter the detailed address including road name. |

* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "NAVER 1784",
  "address": {
    "@type": "PostalAddress",
    "postalCode": "13561",
    "addressRegion": "경기",
    "addressLocality": "성남시 분당구",
    "streetAddress": "정자일로 95"
  }
}
</script>
```
* Example implemented in Microdata format
```html
<div itemscope itemtype="https://schema.org/Organization">
  <span itemprop="name">NAVER 1784</span>
  <div itemprop="address" itemscope itemtype="https://schema.org/PostalAddress">
    <span itemprop="postalCode">13561</span>
    <span itemprop="addressRegion">경기</span>
    <span itemprop="addressLocality">성남시 분당구</span>
    <span itemprop="streetAddress">정자일로 95</span>
  </div>
</div>
```
