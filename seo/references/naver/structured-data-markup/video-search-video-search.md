# Video search (Video Search)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-video)

## Guide to structuring and collecting video search data

Naver video search provides not only Naver's video service, but also videos from external services through collection as search results.

If you would like your information to be exposed in Naver video search, please follow the procedures below to apply for application and partnership offers.

### Video data overview

   * Target Type: Two types of data are required: Video and Channel.
   * Data format: Please write in JSON-LD format according to the schema defined in [schema.org](https://schema.org).
        *   Video :  [VideoObject](https://schema.org/VideoObject)
        *   Channel :  [Person](https://schema.org/Person)


**1. Relationship between Video and Channel**
   * Video document: Represents an individual video detail page, and the top @type is VideoObject.
   * Channel document: Represents a channel page, with the top-level @type being Person.
   * Channel information in video documents is written in creator (Person). creator.name is the channel name, creator.url is the channel page URL, and uses the same values ​​as name·url in a separate Channel document. The channel ID cid also uses the same value in both documents.
   * Channels are always written as Person. 'Channel' in Naver video search refers to the unit for uploading videos, and broadcasting program, organization, and brand channels are all written as Person (not TVSeries, Organization, or ProfilePage).

```
VideoObject
├─ name  : 영상 제목
├─ url   : 영상 상세 페이지
├─ cid   : 채널 ID (Channel 문서의 cid와 동일)
└─ creator (Person)
   ├─ name : 채널 이름
   └─ url  : 채널 페이지 URL

Channel (Person)
├─ name : 위 creator.name과 동일
├─ url  : 위 creator.url과 동일
└─ cid  : 위 VideoObject.cid와 동일
```

**2. Page structure**
   * Create one top-level VideoObject on the video detail page and one top-level Person on the channel page.
   * Other types of JSON-LD (TVSeries, BreadcrumbList, etc.) on the same page are not used for collection.
   * Avoid creating multiple VideoObjects on one page. Playlist/list pages are not subject to collection.
   * Write it as a single object instead of enclosing it with @graph.

**3. Things to keep in mind when writing**
   * Channel name and URL are written in the creator (Person) object.
   * Do not add channelName and channelUrl as flat properties at the top of the VideoObject. The outer name is the video title, creator.name is the channel name, and creator.url is the channel page URL.
   * Conversely, cid·mobileUrl·mobileChannelUrl are Naver extended properties written at the top of VideoObject. Don't put it in creator.

✅ Correct example — Channel name/URL is in the creator object, cid is at the top level.

```
{
  "@type": "VideoObject",
  "name": "여름 캠핑 브이로그",
  "cid": "minsu",
  "creator": {
    "@type": "Person",
    "name": "캠핑하는 민수",
    "url": "https://example.com/channels/minsu"
  }
}
```

❌ Bad example — writing channel information at the top

```
{
  "@type": "VideoObject",
  "name": "여름 캠핑 브이로그",
  "channelName": "캠핑하는 민수",
  "channelUrl": "https://example.com/channels/minsu"
}
```

**[Confirmed during inspection]**
Check during inspection: Check whether creator is an object, creator.@type is Person, and channel name and URL are in creator.name and creator.url, respectively.

### How to apply for document collection
  * Please refer to this document, fill out the data, and apply by filling out [Naver partnership proposal](https://www.navercorp.com/company/partnerApply).
       * Area of ​​partnership desired: Service content partnership
       * Detailed area: Video content partnership
  * Please apply by referring to the API specification in the https://searchadvisor.naver.com/guide/crawl-request-api document.
  * When you push the URL to be collected, Naver's collection robot collects the data by pulling the content data.
  * The three URLs below must be identical for submission URLs.
        1.	URL displayed in search results
        2.	URL rendered by browser
        3.	URL containing structured data (schema.org)
   * If you do not want to expose structured data to all users, you can set it to be included and returned only when accessing the User-Agent used by the Naver collection robot.
   * The faster the data update cycle, the better, but please adjust the update cycle according to the overall document size and operational situation.
   * To use the crawl request API, you must first proceed with [Verify site ownership](../faq/site-registration-and-ownership-verification.md) to Search Advisor.
Refer to the [Crawl request API specification and integration](../partner-api/crawl-request-api-specification-and-integration.md) guide to start linking the web page's crawl request API.
   * After the partnership application and [Schema.org](https://schema.org/) markup development are completed, if you apply for partnership, we will provide partnership review and testing support.


**[Collection application flow]**
* Prepare the video detail page and channel page and ensure that the collection robot can access them.
* Create schema.org-compliant JSON-LD for each page.
* Align the search result display URL, browser rendering URL, and structured data URL to be the same.
* After confirming site ownership, push the target URL to the crawl request API.
* After collection, we verify that the structured data is parsed properly and matches the actual page content.


### Considerations for Transitioning Document Collection
  * Please refer to the [Setting up robots.txt](../seo-basics/configuring-robots-txt.md) guide and allow Naver Robot to collect related documents and attached pages such as thumbnails in the site's robots.txt.
  * Paid videos: Videos with offers are considered paid and excluded from search results. Do not write offers for free videos as it is judged solely on the presence of offers regardless of the price value. (See “Paid Video Examples” below)
  * Videos requiring login: If indexing is required, prior consultation is required.
  * How to disallow search: For documents that do not require search exposure, please refer to [Markup Guide\(Preferred URLs and Robot Meta Tags\)](../html-markup/preferred-urls-and-robots-meta-tags.md), apply noindex to the meta tag, and request a re-collection push.


## data format

In JSON-LD, write the name exactly as it is in the 'JSON-LD creation location' column in the table below. Do not create properties that are not in the table (e.g. channelName, channelUrl).

[Naver Extension] The properties (cid, mobileUrl, mobileChannelUrl, adultYn of the channel) are not schema.org standards, so a warning may be issued by the schema.org verification tool. This is normal, do not rename or move it to another property (identifier, additionalProperty, etc.), just write it where it appears in the table.


### How to read a table
|heat|meaning|
| --- | --- |
|name |This is the Korean name of the item. It's not a JSON-LD key.|
|Where to write JSON-LD|The full path from the top of the document. In JSON-LD, write the exact name of this column. [Naver Extension] is a Naver-specific property, not a schema.org standard.|
|form|The type, format, and allowed values ​​of the value.|
|essential|Required / Conditional / Optional. Conditional = Required if the condition written in the Description column is met.|
|explanation|The meaning of the value, whether or not it is displayed in search results, the value that must be the same as other documents, and what happens when it is omitted.|
|example|This is the same value as the sample below.|

### Information to be submitted when applying for partnership
The information below is not written in JSON-LD, but is delivered separately as a fixed value per source when applying for partnership.

|name|form|explanation|example|
| --- | --- | --- | --- |
|Provider name| string |Exposure to ‘source’ in search results  | "NAVER" |
| Provider URL | string url |Exposure to ‘source’ in search results  | " https://www.naver.com" |
| Is it an official channel? | yes/no |Are all the channels provided by the provider official (operated by broadcasters/institutions)? Specified collectively by provider and not separated by document  | yes |



### Video
Top-level @type: VideoObject. Sorted in the following order: Required → Conditional → Optional.

|name|Where to write JSON-LD|form|essential|explanation|example|
| --- | --- | --- | --- | --- | --- |
| document type | `@type` | Fixed value `VideoObject` | essential | Indicates video detail page | `"VideoObject"` |
| video title | `name` | string | essential | Just write the video title. **Site name/service name suffix (e.g. `\| NAVER`) prohibited.** If the episode is part of the title, it can be included. Displayed as search result title | `"여름 캠핑 브이로그 1화"` |
| Video description | `description` | string | essential | Must match the description the user can see on the video page | `"첫 캠핑지에 도착해…"` |
| Video URL (PC) | `url` | string url | essential | **Must be the same** as search exposure/browser rendering/structured data URL (refer to ‘How to apply for document collection’) | `"https://example.com/videos/1001"` |
| Representative thumbnail | `thumbnailUrl` | String URL (**String recommended**, if array use first value) | essential | Representative thumbnail image URL. If value is missing, use `og:image` from page instead | `"https://example.com/thumb/1001.jpg"` |
| Upload date and time | `uploadDate` | String, **ISO-8601, with seconds + timezone** ( `YYYY-MM-DDThh:mm:ss+09:00` or `…Z` ) | essential | **Time the video was posted on the site**. Exposure to search results | `"2026-07-02T09:00:00+09:00"` |
| playing time | `duration` | String, ISO-8601 duration | essential | Total playing time (can include time units `H`) | `"PT29M5S"` |
| channel id | `cid`   `[네이버 확장]` | string | essential | A unique and **immutable** ID for each channel **within the provider** (we recommend using the ID in the channel URL path). **Same value as `cid` in the relevant Channel document** | `"minsu"` |
| Channel information type | `creator.@type` | Fixed value `Person` | essential | Broadcasting company/organization channels are also written as `Person` (not `Organization`) | `"Person"` |
| channel name | `creator.name` | string | essential | Channel (program) name only. **Same value as `name` in the Channel document**. Exposure as ‘channel’ in search results | `"캠핑하는 민수"` |
| Channel URL (PC) | `creator.url` | string url | essential | A separate page URL showing the channel. **Same value as `url` in Channel document** | `"https://example.com/channels/minsu"` |
| Rating | `contentRating` | String, allowed values ​​**`"12+"` / `"15+"` / `"18+"` ** | conditional | Videos with viewing age restrictions are required. **If omitted, it is treated as general admission price**. ** `"18+"` is treated as adult content** (the domestic rating not suitable for young people is also written as `"18+"`).  Flag values ​​such as `0` / `1` or other notations are not used. | `"15+"` |
| Mobile video URL | `mobileUrl`   `[네이버 확장]` | string url | select | Created when there is a separate mobile page. If omitted, it is processed as a PC URL. | `"https://m.example.com/videos/1001"` |
| Mobile Channel URL | `mobileChannelUrl`   `[네이버 확장]` | string url | select | Created when there is a separate mobile channel page. If omitted, it is processed as a PC URL. | `"https://m.example.com/channels/minsu"` |
| keyword | `keywords` | Comma-separated string or array of strings | select | Keywords that describe the video well in order of importance | `"캠핑, 브이로그, 텐트"` |
| video horizontal size | `width` | number (px) | select | For vertical video classification. Omit if not necessary | `1920` |
| video vertical size | `height` | number (px) | select | For vertical video classification. Omit if not necessary | `1080` |
| Category | `additionalType` | String (free value, no set code) | select | Video classification category. Recommended organization such as categories in channel documents | `"travel"` |
| paid information | `offers`  ( `@type` :  `Offer` ,  `price` ,  `priceCurrency` ,  `availability` ) | object or array of objects | conditional | **Only written for paid videos.** If `offers` is present, it is considered a paid video and **excluded from search results**. Regardless of the price/`availability` value, it is judged solely on the presence of `offers`, so **Do not write in free videos** (including 0 won offers). If there are multiple offers, such as single items or vouchers, write them in an array. | “Paid video example” below |
| Views | `interactionStatistic[].userInteractionCount`  ( `interactionType.@type`  =  `http://schema.org/WatchAction` ) | number. ** `interactionType` must be written as an object (`{"@type": …}`)** (Do not use string IRI format) | select | Ranking reference | `1000` |
| number of likes | `interactionStatistic[].userInteractionCount`  ( `interactionType.@type`  =  `http://schema.org/LikeAction` ) | number.  `interactionType` is written as an object | select | Ranking reference | `100` |
| number of comments | `interactionStatistic[].userInteractionCount`  ( `interactionType.@type`  =  `http://schema.org/CommentAction` ) | number.  `interactionType` is written as an object | select | Ranking reference | `10` |


#### sample

```
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "VideoObject",
  "name": "여름 캠핑 브이로그 1화",
  "description": "첫 캠핑지에 도착해 텐트를 치는 과정을 담았습니다.",
  "url": "https://example.com/videos/1001",
  "mobileUrl": "https://m.example.com/videos/1001",
  "thumbnailUrl": "https://example.com/thumb/1001.jpg",
  "uploadDate": "2026-07-02T09:00:00+09:00",
  "duration": "PT29M5S",
  "contentRating": "15+",
  "cid": "minsu",
  "mobileChannelUrl": "https://m.example.com/channels/minsu",
  "creator": {
    "@type": "Person",
    "name": "캠핑하는 민수",
    "url": "https://example.com/channels/minsu"
  },
  "keywords": "캠핑, 브이로그, 텐트",
  "width": 1920,
  "height": 1080,
  "additionalType": "travel",
  "interactionStatistic": [
    { "@type": "InteractionCounter", "interactionType": { "@type": "http://schema.org/WatchAction" }, "userInteractionCount": 1000 },
    { "@type": "InteractionCounter", "interactionType": { "@type": "http://schema.org/LikeAction" }, "userInteractionCount": 100 },
    { "@type": "InteractionCounter", "interactionType": { "@type": "http://schema.org/CommentAction" }, "userInteractionCount": 10 }
  ]
}
</script>
```

#### Paid video example
Just add offers to the video sample above — this video will be excluded from search results
```
{
  "offers": [
    { "@type": "Offer", "price": "2200", "priceCurrency": "KRW", "availability": "https://schema.org/InStock" },
    { "@type": "Offer", "price": "9900", "priceCurrency": "KRW", "availability": "https://schema.org/InStock" }
  ]
}
```

### Channel
Top-level @type: Person. Sorted in the following order: Required → Conditional → Optional.

|name|Where to write JSON-LD|form|essential|explanation|example|
| --- | --- | --- | --- | --- | --- |
| document type | `@type` | Fixed value Person | essential | Broadcasting programs, organizations, and brand channels are **Must** be Person (not TVSeries, Organization, or ProfilePage) | "Person" |
| channel name | `name` | string | essential | Channel name only (no site name/service name suffix). Same value as creator.name in Video | “Minsu camping” |
| Channel URL (PC) | `url` | string url | essential | Channel page URL. Same value as creator.url of video | " https://example.com/channels/minsu" |
| channel id | `cid` [Naver Extension] | string | essential | A unique and unchanging ID for each channel within the provider. Same value as cid of video | "minsu" |
| Channel Description | `description` | string | essential | Channel introduction | “Camping sites across the country every weekend…” |
| Channel creation date | `mainEntityOfPage.dateCreated`  ( `mainEntityOfPage.@type`  =  `CreativeWork` ) | String, ISO-8601, seconds + timezone required (YYYY-MM-DDThh:mm:ss+09:00 or …Z) | essential | Channel creation time. Date not recognized if seconds or timezone are missing | "2025-11-20T15:30:00+09:00" |
| Channel information modification date | `mainEntityOfPage.dateModified` | string, ISO-8601, seconds + timezone required | essential | Channel information modification time. Format condition is same as creation date | "2026-07-06T10:55:00+09:00" |
| Adult channel or not? | `adultYn` [Naver Extension] (Top) | String, "1" (adult) / "0" (non-adult) | conditional | “1” is required for adult channels. If omitted, treated as non-adult. It is not recognized if written inside identifier(PropertyValue). | "0" |
| keyword | `keywords` | Comma-separated string or array of strings | select | Keywords that well describe the channel in order of importance | “Camping, vlogging, travel” |
| Category | `additionalType` | String (free value, no set code) | select | Channel classification category. Use as channel genre in search results | "travel" |
| number of subscribers | `interactionStatistic[].userInteractionCount`  ( `interactionType.@type`  =  `http://schema.org/FollowAction` ) | number. interactionType is written as an object | select | Number of Channel Subscribers | 1000 |

#### sample
The channel page is also created by <meta property="og:image" content="…">.

```
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "Person",
  "name": "캠핑하는 민수",
  "url": "https://example.com/channels/minsu",
  "cid": "minsu",
  "description": "주말마다 전국 캠핑장을 다니는 캠핑 채널입니다.",
  "mainEntityOfPage": {
    "@type": "CreativeWork",
    "dateCreated": "2025-11-20T15:30:00+09:00",
    "dateModified": "2026-07-06T10:55:00+09:00"
  },
  "adultYn": "0",
  "keywords": "캠핑, 브이로그, 여행",
  "additionalType": "travel",
  "interactionStatistic": [
    { "@type": "InteractionCounter", "interactionType": { "@type": "http://schema.org/FollowAction" }, "userInteractionCount": 1000 }
  ]
}
</script>
```

* Validate the markup with a [JSON syntax checker](https://jsonformatter.curiousconcept.com/) and the [Schema.org validator](https://validator.schema.org/). Warnings about Naver extension properties in the Schema.org validator are expected.

#### common mistakes

|❌ Wrong writing|✅ Correct writing|
| --- | --- |
| Write `creator` as Organization (broadcasting company) | `creator` means **channel** → Person + channel (program) name·URL. Broadcasting company information is written at `publisher` |
| Mixed use of URLs (`url` is https, `og:url`·canonical is http) | Unify exposure, rendering, and structured data URL into one |
| VideoObject at the top level is `channelName` , `channelUrl` | `creator: { "@type": "Person", "name": …, "url": … }` |
| Writing `캠핑하는 민수 \| 네이버TV` in the channel `name` | Use the channel name alone: `캠핑하는 민수` |
| Channel document `@type` this `TVSeries` | `"@type": "Person"` |
| At the top of the channel document is `createDate` / `modifyDate` , format `2025-11-20 15:30` | `mainEntityOfPage.dateCreated` / `dateModified`, `2025-11-20T15:30:00+09:00` (including seconds and timezone) |

### Verification checklist before requesting collection

☐ Confirm that the JSON syntax is valid and that `@context` is `https://schema.org/`.
☐ Make sure there is one top-level VideoObject (video detail page) or Person (channel page) per page.
☐ Make sure you write the video title in VideoObject.name and the channel name in creator.name.
☐ Checks if creator is an object and creator.@type is Person.
☐ Check that you have not arbitrarily added properties that are not in the table, such as channelName, channelUrl, and creatorName.
☐ Check whether creator.name·creator.url and the name·url of the separate Channel document match.
☐ Check whether cid is the same value in the Video document and the Channel document.
☐ Make sure the date is ISO-8601 including seconds and timezone (e.g. 2026-07-02T09:00:00+09:00).
☐ Make sure there are no offers in the free video.
☐ Check if og:image is present on the channel page.
☐ Verify that the values ​​in JSON-LD match what the user sees on the actual page.
☐ Make sure that the search result display URL, browser rendering URL, and structured data URL are the same.
☐ Check the noindex and robot access policies for documents you do not want to collect.
☐ After requesting collection, check whether structured data is parsed normally.
