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

{% tab title="Sol2" %}
### Questions:

```fsharp
Input ----> Process --> Output

Input: 
 - Source? // File System / DB 
 - Large Dataset? // Yes


Process:
 - Crawl?
   - Onetime crawling or Run Cron Job (get updated content every few mins) ?
   - Specific Content Type? // HTML, jpg, mp3
   - Consider external domain URL while scaning?
   - Handle SPA or Frontend-Rendering ?

 - Scalability // Yes, as fast as possible


Output:
- Pupose? // Decide based on the use case
   
// 1. if it is faster lookup  - Search Engine: (we need to Index the output and lookup faster)
 - Elasticsearch or (ELK) Stack — Elasticsearch Logstash Kibana, Beats
 - Store: MetaData in Database & actual file in BlobStorage (S3)
 - Distributed File System // Big Table or HDFS


// 2. If it is not a faster lookup
 - File System or Blob Storage // S3
```

### Key Components:

```fsharp
#1. URL Reader

#2. URL Queue // addUrlsinQueu

#3. URL Filter
    --> Filter Invalid URLs
    --> Filter Duplicate URLs
        --> BloomFilter 
            --> Check: URL Store (Redis / NoSQL DB)
        

#4. Crawl Queue
    --> Crawl Status Store

#5. Crawler
    --> DNS Cacher
    --> Fetchers, (Render SPA in Server)
    --> HTML Parser
        ==> HTML Content Extracter
        --> GOTO: 6 // addContentInOuputQueue
            --> SUCCESS: Update: Crawl Status Store // 'contentAddedInOuputQueue:true' 
            --> FAILURE: Update: 'retryCount' in Crawl Status Store // addBackThisUrlIntoCrawlQueue
            
        ==> URL Extractor
        --> URL Sanitizer 
        --> GOTO: 2 // addUrlsInUrlQueue
            --> SUCCESS: Add/Update: URL Store (Redis / NoSQL DB)
            --> FAILURE: Add: back into Crawl Queue
            
        
#6. Output Queue

#7. Output Filter (duplicateContentFilter) // SimHash

#8. Output Writer
    --> Content Store
        ==> DB(metadata)
        ==> S3(File)
```

### Advanced Crawler -Capabilities:

```fsharp
Advanced Crawlers needs this below behavior
- Freshness // crawlFrequency
- Politeness // giveSomeWaitTimeForEachDomain


#Option1: URL Frontier: 
 - provides 'Priorities', 'Freshness' & 'Politeness' capability


#Option2: Bull (Redis based queue):****
 - also provides below capabilities
   - Concurrency
   - 'Priorities'
   - 'Delayed jobs'  // we can use it for 'Politeness'
   - Repeatable jobs
   - Rate Limiter
```

### Filter Duplicate URLs:

```fsharp

#Option1: NoSQL DB Lookup

DS: { fullUrlHash: crawlInfo } // notEffiecient: soonHashCollision
DS: { domainUrlHash: [ ...urlHashes ]  } // effiecient: lessHashCollision // bucketByDomainUrl

urlHash: { fullUrlHash: { ...crawlInfo } }
crawlInfo: { crawlStatus: 'READY/STARTED/IN-PROCESS/SUCCESS/FAILED', retryCount: 2, lastCrawlDate: ''}



#Option2: BloomFilter + NoSQL DB Lookup
- BloomFilter // firstLevelFilter // canQuicklyTellIfNotAvailable
    - ifNotAvailable // 100% GURANTEED
    - ifAvailable // NOT 100% GURANTEE
        - lookupInDB
```

XXXX

![](../../../.gitbook/assets/image%20%287%29.png)

![](../../../.gitbook/assets/image%20%281%29.png)
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

## 

## [5. Design Phone Directory](https://leetcode.com/problems/design-phone-directory)

{% tabs %}
{% tab title="Question" %}
379. Design Phone Directory

Design a Phone Directory which supports the following operations:

1. `get`: Provide a number which is not assigned to anyone.
2. `check`: Check if a number is available or not.
3. `release`: Recycle or release a number.
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript

class PhoneDirectory {
  constructor(maxNumbers) {
    this.len = maxNumbers;
    this.availableNumbers = new Set();
    for (let i = 0; i < maxNumbers; i++) {
      this.availableNumbers.add(i);
    }
    // console.log(this.availableNumbers);
  }

  get() {
    if (this.availableNumbers.size === 0) return -1;
    const nextAvailableNo = this.availableNumbers.values().next().value;
    this.availableNumbers.delete(nextAvailableNo);
    return nextAvailableNo;
  }

  check(number) {
    return this.availableNumbers.has(number);
  }

  release(number) {
    this.availableNumbers.add(number);
  }
}

// Init a phone pd containing a total of 3 numbers: 0, 1, and 2.
const pd = new PhoneDirectory(3);

// It can return any available phone number. Here we assume it returns 0.
console.log(pd.get());

// Assume it returns 1.
console.log(pd.get());

// The number 2 is available, so return true.
console.log(pd.check(2));

// It returns 2, the only number that is left.
console.log(pd.get());

// The number 2 is no longer available, so return false.
console.log(pd.check(2));

// Release number 2 back to the pool.
pd.release(2);

// Number 2 is available again, return true.
console.log(pd.check(2));

```
{% endtab %}
{% endtabs %}

...

## [6. Design Hit Counter](https://leetcode.com/problems/design-hit-counter)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/178662/Design-a-Hit-Counter](https://leetcode.com/discuss/interview-question/178662/Design-a-Hit-Counter)
* [https://leetcode.com/discuss/interview-question/124821/Dropbox-or-Design-Hit-Counter](https://leetcode.com/discuss/interview-question/124821/Dropbox-or-Design-Hit-Counter)
* Design a Hit Counter 
  * write a program to count how many times a web page has been accessed in the last 5 minutes.  
  * First question was about how to implement get\_hits and log\_hits methods for a website visitors, where get\_hits would return the number of hits in last 5 minutes.
* Follow up question was how to scale this as a service when billions of concurrent Users may be hitting and thus log\_hits will be called that often.
* Write methods to log hits and get number of hits in past 'x' minutes.
{% endtab %}

{% tab title="Video" %}
Implementation: 

* [https://www.youtube.com/watch?v=vMB0XjFpt\_s](https://www.youtube.com/watch?v=vMB0XjFpt_s) 

System Design:\(Rate Limit\) 

* [https://www.youtube.com/watch?v=xrizarXJgC8](https://www.youtube.com/watch?v=xrizarXJgC8)
* [https://www.youtube.com/watch?v=mhUQe4BKZXs](https://www.youtube.com/watch?v=mhUQe4BKZXs)
{% endtab %}

{% tab title="Code" %}
```javascript
/*
https://leetcode.com/problems/design-hit-counter/discuss/83483/Super-easy-design-O(1)-hit()-O(s)-getHits()-no-fancy-data-structure-is-needed!

What is 300? we need only past 5mins  // 5*60sec ==> 300sec
For each second (timestamp), we are counting an entry

TC: 
  -hit(): O(1)      
  -getHits(): O(1)
SC: O(1)

// since we always store & get '300' items O(1) // remember: 300 is constant
// but if we consider 300 is an input, 
  -- then it should be O(s) // s is seconds (past 5 minutes = 5x60sec ==> 300sec)
*/
class HitCounter {
  constructor() {
    this.hits = [];  // new Array(300);
  }
  hit(timestamp) {
    let index = timestamp % 300;
    const hitEntry = this.hits[index];
    if (hitEntry && hitEntry.timestamp === timestamp) {
      hitEntry.count = hitEntry.count + 1;
    } else {
      this.hits[index] = { timestamp, count: 1 };
    }
  }
  getHits = function(curTimestamp) {
    let counter = 0;
    for (let hitEntry of this.hits) {
      if (hitEntry) {
        const timestampFromNow = curTimestamp - hitEntry.timestamp;
        if (timestampFromNow < 300) {
          // count: only applicable timestamp (within 5mins)
          counter = counter + hitEntry.count;
        }
      }
    }

    return counter;
  };
}

```
{% endtab %}

{% tab title="Exe" %}
```
const counter = new HitCounter();

// hit at timestamp 1.
counter.hit(1);

// hit at timestamp 2.
counter.hit(2);

// hit at timestamp 3.
counter.hit(3);

// get hits at timestamp 4, should return 3.
console.log(counter.getHits(4));

// hit at timestamp 300.
counter.hit(300);

// get hits at timestamp 300, should return 4.
console.log(counter.getHits(300));

// get hits at timestamp 301, should return 3.
console.log(counter.getHits(301));

// hit at timestamp 350.
counter.hit(350);

console.log(counter.getHits(600)); // 1
```
{% endtab %}
{% endtabs %}

...

## [12. Design Search Autocomplete System](https://leetcode.com/problems/design-search-autocomplete-system)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/366628/Dropbox-or-OA-2019-or-Auto-complete-feature](https://leetcode.com/discuss/interview-question/366628/Dropbox-or-OA-2019-or-Auto-complete-feature)
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## 

