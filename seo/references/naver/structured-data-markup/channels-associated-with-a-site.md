# Channels associated with a site

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-channel)

### Site related channels
* Naver services and SNS channels related to the site can be expressed as structured data and notified to the crawler.

* In order to provide highly satisfactory search results, Naver's search engine sometimes uses an automated algorithm to analyze the linkage between sites and channels.
   * Clustering by automatically extracting link structure and text information between channels
   * Recognizable and relevant channel markup - structured data written on the root page of your site
* Information collected through these various channels is not guaranteed to be exposed in the results, but may be partially expressed in cases where the engine determines that user convenience is high.
   * Site with a unique name without ambiguity
   * A highly reliable site that can provide the correct answer to anyone with public information such as government agencies
   * Sites with high user preference
* The related channel domains used in the current analysis are as follows. (Support channels may change depending on circumstances.)
   * Naver Service
     * Naver Blog, Smart Store, Knowledge iN, Chijijik, Clip
   * web channel
     * Carrot, Thread, Instagram, YouTube, Kakao Story, Kakao Talk Channel, Tistory, TikTok, Facebook, X (Twitter)

![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfNzcg/MDAxNzkyMDQ5NTI3MTA5.1KalQfzi_AJ2CCAYAlrj8WFXt8E0SAaQqlFZ7Y0ViZUg.79qfFpT99IVtStIM_lUKroG1w9t5Rp9_iyXlo_xiuUcg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EC%82%AC%EC%9D%B4%ED%8A%B8%EC%97%B0%EA%B4%80%EC%B1%84%EB%84%90.png)

### Site-related channel markup
* Types and Properties
  Use [Person](https://schema.org/Person) or [Organization](https://schema.org/Organization) defined by schema.org and specify the property values ​​below.

| attribute | Required? | explanation |
| --- | --- | --- |
| name | essential | site name |
| url | essential | Site URL |
| sameAs | essential | List of channel URLs associated with your site |
* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
 "@context": "http://schema.org",
 "@type": "Person",
 "name": "My Site Name",
 "url": "http://www.mysite.com",
 "sameAs": [
   "https://www.facebook.com/myfacebook",
   "http://blog.naver.com/myblog",
   "http://smartstore.naver.com/mystore"
 ]
}
</script>
```
* Example implemented in Microdata format
```
<span itemscope="" itemtype="http://schema.org/Organization">
<link itemprop="url" href="http://www.mysite.com">
<a itemprop="sameAs" href="https://www.facebook.com/myfacebook"></a>
<a itemprop="sameAs" href="http://blog.naver.com/myblog"></a>
<a itemprop="sameAs" href="http://smartstore.naver.com/mystore"></a>
</span>
