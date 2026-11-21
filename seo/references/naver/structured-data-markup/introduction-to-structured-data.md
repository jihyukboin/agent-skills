# Introduction to structured data

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-intro)

### Naver Search and Structured Data
Structured data refers to data processed by logically organizing content containing various information, and a representative example is a relational database. From a search engine's perspective, it is of great help in interpreting the content of a web document if it has an organized structure.

Efforts to define web content as structured data have been steadily progressing through the efforts of the Internet community and related companies, and the results are being disseminated through the schema.org site. Structured data defined by schema.org was officially incorporated within the web standards organization W3C in 2015, and standardization activities are actively underway as one of the web standards.

Naver utilizes structured data to configure and provide search results tailored to content characteristics. Structured data is data added to a web page by structuring information about specific content into detailed attributes appropriate for the type of content. Naver crawler automatically collects this information, organizes the information according to the characteristics of the content, and uses it to reflect searches.

> ❗ Even if structured data is properly marked up, it is not guaranteed to be reflected in search results. Depending on the content within the page, different information may be displayed depending on what is most appropriate.

#### schema.org
The structured data presented by schema.org consists of data types and properties. A data type is a combination of properties according to the characteristics of a web page or content, and structured data can be added to one web page by combining two or more data types. A list of data types defined by schema.org can be found at schema.org vocabulary.

Attributes are details of a web page or content that make up a data type. For example, in the case of audio content, playback time, number of plays, etc. can be considered information corresponding to properties.

#### Select language format
* Schema.org's structured data supports three language formats: Microdata, RDFa, and JSON-LD. Naver recommends using the widely used Microdata format or JSON-LD format.

* The following code is an example of structured data written in JSON-LD format and contains structured data about a music file. Examples written in other language formats can be found on schema.org's detailed pages for each data type.

```

<script type="application/ld+json">
{
"@context": "http://schema.org",
"@type": "AudioObject",
"contentUrl": "http://media.freesound.org/data/0/previews/719__elmomo__12oclock_girona_preview.mp3",
"description": "Recorded on a terrace of Girona a sunday morning",
"duration": "T0M15S",
"encodingFormat": "mp3",
"name": "12oclock_girona.mp3"
}
</script>
```

### public testing tools
* Data verification is required to ensure that structured data has been applied correctly. When validating structured data, use [Structured data testing tool](https://validator.schema.org/) provided by schema.org.
