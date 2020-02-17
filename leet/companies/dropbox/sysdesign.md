# SysDesign

## [8. Web Crawler](https://leetcode.com/problems/web-crawler)

{% tabs %}
{% tab title="Question" %}
Given a url `startUrl` and an interface `HtmlParser`, implement a web crawler to crawl all links that are under the **same hostname** as `startUrl`. 

Return all urls obtained by your web crawler in **any** order.

Your crawler should:

* Start from the page: `startUrl`
* Call `HtmlParser.getUrls(url)` to get all urls from a webpage of given url.
* Do not crawl the same link twice.
* Explore only the links that are under the **same hostname** as `startUrl`.

```javascript
Example1
---------
Input:
urls = [
  "http://news.yahoo.com",
  "http://news.yahoo.com/news",
  "http://news.yahoo.com/news/topics/",
  "http://news.google.com",
  "http://news.yahoo.com/us"
]
// edges = [[2,0],[2,1],[3,2],[3,1],[0,4]]
startUrl = "http://news.yahoo.com/news/topics/"
Output: [
  "http://news.yahoo.com",
  "http://news.yahoo.com/news",
  "http://news.yahoo.com/news/topics/",
  "http://news.yahoo.com/us"
]

Example2
---------
Input: 
urls = [
  "http://news.yahoo.com",
  "http://news.yahoo.com/news",
  "http://news.yahoo.com/news/topics/",
  "http://news.google.com"
]
// edges = [[0,2],[2,1],[3,2],[3,1],[3,0]]
startUrl = "http://news.google.com"
Output: ["http://news.google.com"]

Explanation: The startUrl links to all other pages that do not share the same hostname.
```
{% endtab %}

{% tab title="More" %}
* Write a program to find all reachable web pages from a given url
{% endtab %}

{% tab title="Code" %}
```javascript
function getDomain(url) {
  // url.split("/")[2]; // shortcut
  const protocolLen = "http://".length;
  let domain = "";
  for (let i = protocolLen; i < url.length; i++) {
    const char = url[i];
    if (char === "/") {
      break;
    }
    domain = domain + char;
  }
  return domain;
}


/*
 
 Using BFS

 * @param {string} startUrl
 * @param {HtmlParser} htmlParser
 * @return {string[]}
 */
function crawl(startUrl, htmlParser) {
  const hostname = getDomain(startUrl);
  const fullHostName = `http://${hostname}`;

  const visitedUrlsSet = new Set([startUrl]);
  const queue = [startUrl]; // TODO: use: LinkedList

  while (queue.length > 0) {
    const currentUrl = queue.shift();
    const childUrls = htmlParser.getUrls(currentUrl);

    for (const url of childUrls) {
      // consider: only not-visited Urls
      if (url.startsWith(fullHostName) && !visitedUrlsSet.has(url)) {
        queue.push(url);
        visitedUrlsSet.add(url);
      }
    }
  }

  return Array.from(visitedUrlsSet);
}



// console.log(crawl("http://news.yahoo.com/news/topics/", { getUrls }));

```
{% endtab %}
{% endtabs %}



## [9. Web Crawler Multithreaded](https://leetcode.com/problems/web-crawler-multithreaded)

{% tabs %}
{% tab title="" %}

{% endtab %}

{% tab title="Qstns?" %}
**SysDesign:**   Input —&gt; Process —&gt; Output  
****

### **Input:**

* Input Source? FileSystem or REST API 
* Huge Dataset?
* Dataset is in order? // each domain has each file or specific section \(any seperators?\)
* Priority Involved? Do we have prioritize some specific websites?

### **Process:**

* Web Crawling is a IO operation // use NIO \(Non-Blocking I/O\) or Async IO
* * **Crawl:**
  * What to crawl ?
    * Specific Content Type? // any specific type of content are we looking or everything \(becoz url can be another html/js/css/mp3/video/…\)
    * Scan all URLs or Sub URLs pages only \(consider external domain?\)
    * Onetime crawling or Run Cron Job \(get updated content every few mins\) ?
    * 
  * How to crawl?
* **Crawl Rules:**
  * Do not crawl duplicate items \(duplicate URLs\)
    * do we consider duplicates in historical data?
      * if yes, use NoSQL database // use Mongo DB  
        * * //Why NoSQL? No relation invloved on each transaction //Eventually Consistent is OK
      * if no, use Redis/Cache store
        * * for faster lookup
    * politeness \(do not overload a website\) // ddos attack
  * * * Multiple Machines Prioritize the Work \(and Read Politely\) 
      * or Multiple Public IPs \(this still overloads the website\)

### **Output:**

* How to store? // Database or File System or Distributed File System \(HDFS\)
{% endtab %}

{% tab title="Sol1" %}
**Distributed Web Crawling System**

```text
Data Structure
    HashMap: { fullUrlKey : {crawlStatus, retryCount, crawlDate} }  // { 'domain1.com/path1':  {crawlStatus: ’READY/STARTED/IN-PROCESS/SUCCESS/FAILED', retryCount: 2, lastCrawlDate: ''}
    HashMap: { domain : [ fullUrlKey1, fullUrlKey2,... ] }  // { 'domain1.com': [ 'domain1.com/path1', 'domain1.com/path2’,…]
    RECOMMEND: It is NOT GOOD to have ‘long-keys’ // use md5 and get hash of each URL and use that as a key  // md5('domain1.com/path1’) // HASHKEY1
    reduces memory and helps in faster lookup


Distributed System // for Horizontal Scaling
```

### **Design:**

#### **1. \[INPUT\]**

* Files / DB 

#### **2. \[URL Reader\]**

---------------read from \[INPUT\] --------------

```text
- Read Input (File Sys) // Since it is bigger file (read chunk by chunk)
- Read parallel // TODO: how to read multiple files effectively?
- Huge Dataset (few files) // one machine to read parallel
- or Huge Dataset (many files) // more machines to read parallel
```

  
---------------add it in \[URL Queue\]------------------

#### **3. \[URL Queue\]**

```text
This helps us buffer (incase if URL store is down, we can still resume the process)
```

#### **4. \[URL Filter\]**

```text
---------------read from [URL Queue]  -----------------
---------------add it in [URL Store]  -----------------
add only if it is new url record 
newRecord: { 'fullUrlOrHash': {crawlStatus: READY, retryCount: 0, crawlDate} }

---------------add it in [Crawl Queue]  -----------------
add only 
if it is new url record 
```

**5. \[URL Store\]**

```text
- NoSQL (MongoDB) or Cache (Redis) // {key:val} database (HashMap DS)
    key: fullURL or md5(fullURL)
    val: {crawlStatus, retryCount, crawlDate}
- This helps us not store duplicate items & maintain crawlStatus & other  metaInfo
```

  
  
**5. \[Crawl Queue\]**

```text
- This help us maintaining crawling order
- Prioritize Items: if required
```

  
  
  
**6. \[Crawler\]**  


```text
---------------read from [Crawl Queue] --------------
Multiple Instances: can read from Crawl Queue

---------------update: {crawlStatus: STARTED} in [URL Store]--------------

use NIO (Non-Blocking I/O) or Async IO
Custom Async DNS Resolver // if OS doesn’t handle this asynchronously 
to get the actual IP address faster
handle: Dos attack
Timer Queue // Each instance will have a timer queue to "Read Politely"
Maintain Map: {urlDomain: nextTimer}
addItInTimerQueue() // setTimeout(task, nextTimer)  
updateNextTimer() //nextTimer = nextTimer + nextTimer
---------update: {crawlStatus: RESCHEDULED} in [URL Store]------------
Use: Multiple Public IPs (to mock server IPs)
```

#### **Tasks:** 

```text
---------------update: {crawlStatus: PROCESSING} in [URL Store]---------------

1. page = fetchFullyRenderedHtmlPage(url)
- if it is a Single Page Application, 
    - renderPageManually(notRenderedPage)
    - use (SSR technique)  jsdom / Puppeteer / Phantom JS  

2. parsedPage = parseHtmlPage(page)  // use: cheeriojs
3. extractRequiredContent(parsedPage)

call customer specific lamda functions or cloud functions
For Extensibility,
for each customer the required contents are different (news, stock, mp3, video,…)
---------------addRequiredContent in [OUTPUT]------------------

4. extractAllUrls(parsedPage) // can go parallel

convert relative URL into an absolute URL 
---------------add all the URLs in [URL Queue]------------------


if all tasks are success,

---------------update: {crawlStatus: COMPLETED} in [URL Store]------------------

if anything failed,
---------------update: {crawlStatus: FAILED} in [URL Store]------------------
{crawlStatus: FAILED, retryCount: retryCount+1}
if crawlRetryCountNotExceeded,
---------------add it in [Crawl Queue]  -----------------
```

  
  
**7. \[OUTPUT\]**

```text
Decide based on the use case:
- if it is faster lookup (Search Engine: (we need to Index the output and lookup faster)

Database
Distributed File System // Big Table or HDFS
Elasticsearch or (ELK) Stack — Elasticsearch Logstash Kibana, Beats
If it is not a faster lookup
Store it in File System
```
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=BKZxZwUgL3Y" %}
{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

