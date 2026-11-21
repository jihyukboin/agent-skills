# Verify requests from Google crawlers and fetchers

[Source: Google](https://developers.google.com/crawling/docs/crawlers-fetchers/verifying-googlebot)

You can verify if a request to your server really is
[from Google](list-of-google-crawlers.md). Verification
is possible for crawlers such as Googlebot, as well as other requests. This is useful if you're
concerned that spammers or other troublemakers are accessing your site while claiming to be from
Google.

Google's crawlers and fetchers fall into three categories:

<table>
<tr>
<th>Type</th>
<th>Description</th>
<th>Reverse DNS mask</th>
<th>IP ranges</th>
</tr>
<tr>
<td><a href="https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers">Common crawlers</a></td>
<td>
      The common crawlers used for Google's products (such as Googlebot). They always respect
      robots.txt rules for automatic crawls.
    </td>
<td>
<code>crawl-***-***-***-***.googlebot.com</code> or
      <code>geo-crawl-***-***-***-***.geo.googlebot.com</code>
</td>
<td><a href="https://developers.google.com/static/crawling/ipranges/common-crawlers.json">common-crawlers.json</a></td>
</tr>
<tr>
<td><a href="https://developers.google.com/crawling/docs/crawlers-fetchers/google-special-case-crawlers">Special-case crawlers</a></td>
<td>
      Crawlers or fetchers that perform specific functions for Google products (such as AdsBot) where there's an
      agreement between the crawled site and the product about the access or for
      abuse-specific crawling or fetching. These crawlers or fetchers may
      or may not respect robots.txt rules.
    </td>
<td><code>rate-limited-proxy-***-***-***-***.google.com</code></td>
<td><a href="https://developers.google.com/static/crawling/ipranges/special-crawlers.json">special-crawlers.json</a></td>
</tr>
<tr>
<td><a href="https://developers.google.com/crawling/docs/crawlers-fetchers/google-user-triggered-fetchers">User-triggered fetchers</a></td>
<td>
      Tools and product functions where the end user triggers a fetch. For example,
      <a href="https://support.google.com/webmasters/answer/9008080">Google Site Verifier</a>
      acts on the request of a user. Because the fetch was requested by a user, these fetchers
      ignore robots.txt rules.<br/>
      Fetchers controlled by Google originate from IPs in the
      <code>user-triggered-fetchers-google.json</code> object and resolve to a
      <code>google.com</code> hostname. IPs in the <code>user-triggered-fetchers.json</code> object
      resolve to <code>gae.googleusercontent.com</code> hostnames. These IPs are used, for example,
      if a site running on Google Cloud (GCP) has a feature that requires fetching external RSS
      feeds on the request of the user of that site.
    </td>
<td>
<code>***-***-***-***.gae.googleusercontent.com</code> or
      <code>google-proxy-***-***-***-***.google.com</code>
</td>
<td>
<a href="https://developers.google.com/static/crawling/ipranges/user-triggered-fetchers.json">user-triggered-fetchers.json</a>,
      <a href="https://developers.google.com/static/crawling/ipranges/user-triggered-fetchers-google.json">user-triggered-fetchers-google.json</a>,
      and <a href="https://developers.google.com/static/crawling/ipranges/user-triggered-agents.json">user-triggered-agents.json</a>
</td>
</tr>
</table>

There are two methods for verifying requests from Google:

- [Manually](https://developers.google.com/crawling/docs/crawlers-fetchers/verifying-googlebot#manual): For one-off lookups, use command line tools. This method is
  sufficient for most use cases.
- [Automatically](https://developers.google.com/crawling/docs/crawlers-fetchers/verifying-googlebot#automatic): For large scale lookups, use an automatic solution to
  match a crawler's IP address against the list of published Google IP addresses.

## Use command line tools

1. Run a reverse DNS lookup on the accessing IP address from your logs, using the
   `host` command.
2. Verify that the domain name is either `googlebot.com`, `google.com`, or
   `googleusercontent.com`.
3. Run a forward DNS lookup on the domain name retrieved in step 1 using the `host`
   command on the retrieved domain name.
4. Verify that it's the same as the original accessing IP address from your logs.

**Example 1:**

```

host 66.249.66.1
1.66.249.66.in-addr.arpa domain name pointer crawl-66-249-66-1.googlebot.com.

host crawl-66-249-66-1.googlebot.com
crawl-66-249-66-1.googlebot.com has address 66.249.66.1
```

**Example 2:**

```

host 35.247.243.240
240.243.247.35.in-addr.arpa domain name pointer geo-crawl-35-247-243-240.geo.googlebot.com.

host geo-crawl-35-247-243-240.geo.googlebot.com
geo-crawl-35-247-243-240.geo.googlebot.com has address 35.247.243.240
```

**Example 3:**

```

host 66.249.90.77
77.90.249.66.in-addr.arpa domain name pointer rate-limited-proxy-66-249-90-77.google.com.

host rate-limited-proxy-66-249-90-77.google.com
rate-limited-proxy-66-249-90-77.google.com has address 66.249.90.77
```

## Use automatic solutions

Alternatively, you can identify Googlebot by IP address by matching the crawler's IP address
to the lists of Google crawlers' and fetchers' IP ranges:

- [Common crawlers like Googlebot](https://developers.google.com/static/crawling/ipranges/common-crawlers.json)
- [Special crawlers like AdsBot](https://developers.google.com/static/crawling/ipranges/special-crawlers.json)
- [User-triggered fetchers (users)](https://developers.google.com/static/crawling/ipranges/user-triggered-fetchers.json)
- [User-triggered fetchers (Google)](https://developers.google.com/static/crawling/ipranges/user-triggered-fetchers-google.json)
- [User-triggered agents](https://developers.google.com/static/crawling/ipranges/user-triggered-agents.json)

For other Google IP addresses from where your site may be accessed (for example,
[Apps Scripts](https://developers.google.com/apps-script)), match the accessing IP address
against the general
[list of Google IP addresses](https://www.gstatic.com/ipranges/goog.json).
Note that the IP addresses in the JSON files are represented in
[CIDR format](https://wikipedia.org/wiki/Classless_Inter-Domain_Routing).
