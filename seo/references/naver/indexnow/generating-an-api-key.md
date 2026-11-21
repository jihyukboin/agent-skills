# Generating an API key

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/indexnow-api-key)

In order for a website administrator to use the IndexNow API, he or she must use a unique key that identifies the owner of the website.
When you create a key file and upload it to a website, the search engine checks the contents of the key and determines whether the website's API use is legal.

One thing to note is that if your website consists of multiple domains, you must use a separate key for each domain.

### Key generation rules

* You must use [UTF-8](https://ko.wikipedia.org/wiki/UTF-8) encoding.
* The key must be created using only letters, numbers, and - used in hexadecimal numbers.
    * a-f, A-F, 0-9, -
* The length of the key is minimum 8 characters and maximum 128 characters.
* The following is an example of key.
    *  fc1e3ad82010475381daf9846e627fdd
    *  eda4094d82454ab0ad8601e3b7405a69

### Post the key on the website

#### ◆ Place it in the root directory of the site (recommended)
Save the file containing the key value as 'same name as key'.txt and upload it to the root directory of the website.

For example, place the key file as follows:
https://www.example.com/aa2451c6c6c64105be9aeb2ae7e541b8.txt
The txt file contains the string aa2451c6c6c64105be9aeb2ae7e541b8.

#### ◆ Place it in the desired directory
In this case, keyLocation information must be specified when requesting the API.
One thing to note is that key information uploaded to a specific directory is only valid when notifying the update of a web page in the same directory.

For example, the key file in http://example.com/catalog/key12457EDd.txt is
Only updates to web pages starting with http://example.com/catalog/ can be notified through the API.
Requests to web pages from other directories are invalid.

### next steps
If the key is correctly placed on the website, you can notify that the web page has been updated through the API.
Next, please refer to the [Request a page update](requesting-page-updates.md) instructions.
