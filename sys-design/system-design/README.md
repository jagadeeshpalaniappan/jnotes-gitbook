# System Design

## Intro

```fsharp
# Distributed System:
------------------------------
- Distributed AppServer(AS):
- Distributed Caching
- Distributed Database

- Microservice Architecture
- Event Driven Architecture (Pub/Sub/EventManger)
- Distributed Data Processing (DFS)
- Distributed Locks


# Distributed System Problems:
------------------------------
- Load Balancing     // Soln: Load Balancers or 'API Gateway'
- Security (Authentication/Authorization) // Soln: API Gateway
- Rate Limiting      // Soln: API Gateway
- Handle Failures    // Soln: Circuit Break Patterns (Hystrix), Bulkhead Pattern

Microservices:
- Service Discovery  // Soln: Service Registry (Eureka Server/Client)
- Debugging/Logging/Tracing // Soln: API Gateway attaches (traceId), Splunk
- Deployment // Soln: CI/CD, Jenkins
- Monitoring // Son: Newrelic, AppDynamics, Splunk



# Event Driven Architecture (Pub/Sub)
------------------------------
    - FaaS // Function as a Service // AWS Lamda, Google Cloud Fn,..
    - Apache Kafka



# Distributed File System 
# Distributed Data Processing
------------------------------
    1. GFS / Hadoop (HDFS) & Run 'MapReduce'
    


# API Gateway: (Tyk, Kong)
------------------------------
- Single Entry Point 
- Security (AuthN/AuthZ, DDos, IP Whitelisting, needNotToExposeMicroserviceIPsOutside)
- Load Balancing
- Dynamic Service Discovery
- Rate Limiting
- Retry / Circuit Break Pattern

- Latency Tracking
- Loggin / Tracing
- Response Caching
- Query Transformation


# API Gateway Problems:
    - SPOF // Soln: Multiple Instances


# Must Discuss:
    - SPOF (Single Point Of Failure)
    - SSOT (Single Source Of Truth)

    
# Load Balancers(LB): (Traefik, NGINX, HAProxy, Seesaw)
------------------------------
    - If we need to use multiple (instances/nodes/machines) 
    - then we need LoadBalancers(LB)
    - Routing Startegy? // How do we route each request?
    
        ## Random: (loadBalance HTTP)
        - ***Round Robin*** // most used
        - Weighted Round Robin (if server1 is double power than server2 & server3) 
        - Least Connection
        - Weighted Least Connection
        
        ## Consistent: (loadBalance DB or CacheNodes)
        - Consistent Hashing
        - Consistent Hashing Ring
```

## Why Distributed System:

```fsharp
# Single Machine Server: (SMS)
Pros:
    - Simple Architecture
    - EasyTo: Maintain,Debug,IndetifyProblem,Fix
Cons:
    - SPOF: Single Point Of Failure
    - Cannot 'Scale' // Vertical Scaling is Limited
    

# Distributed System: (DIS)
Pros:
    - Can 'Scale' without any limits
Cons:
    - Complex Architecture
    - DifficultTo: Maintain,Debug,IndetifyProblem,Fix


---------------------------------------------------------------
                    More Detailed: (SRAEM)
---------------------------------------------------------------


# Scalability: // increasedTraffic or increasedDataSet ==> sysAbleToHandle: withoutAffectingPerformance
- SMS: // VerticallyScalable, LimitedScaling
- DIS: // HorizontallyScalable

# Reliability: // probability of a systemFailure
- SMS: // lessReliable, SPOF
- DIS: // moreReliable, redundancy: oneFailsAnotherCanTakeOver

# Availability: // system remains operational
- SMS: // lessAvailable, SPOF
- DIS: // moreReliable, redundancy: oneFailsAnotherCanTakeOver

// If a system is reliable, it is available. 
// - However, if it is available, it is not necessarily reliable. 
// In other words, 
// - high reliability contributes to high availability, 
// - but it is possible to achieve a high availability even with an unreliable product

# Efficiency:
// how to measure the efficiency of a distributed system
// 1. `Response Time (or latency)` // delay to obtain the first item
// 2. `Throughput (or bandwidth)` // no of items delivered in a given time unit (per second)

- SMS: // lessEfficient
- DIS: // moreEfficient

# Serviceability / Manageability / Maintainability:
- SMS: // easyTo: manage, repair, diagnosing/debug/identify-the-problem, fix/update-the-system 
- DIS: // difficultTo: manage, repair, diagnosing/debug/identify-the-problem, fix/update-the-system



```

##

{% tabs %}
{% tab title="First Tab" %}


```fsharp
```
{% endtab %}

{% tab title="Second Tab" %}
## Handle Failure in Distributed Environment

*   **Circuit Breaker Pattern** - Fault Tolerant Microservices

    * [https://www.youtube.com/watch?v=ADHcBxEXvFA](https://www.youtube.com/watch?v=ADHcBxEXvFA)
    * Libs: Hystrix (maintenance mode), resilience4j


* **Bulkhead Pattern** - Fault Tolerant Microservices
  * [https://www.youtube.com/watch?v=R2FT5edyKOg](https://www.youtube.com/watch?v=R2FT5edyKOg)
  * Libs: Hystrix (maintenance mode), resilience4j
* ...


{% endtab %}
{% endtabs %}

## AppServer(AS):

```fsharp
# Load Balancing (LB) // uniformlyDistributeLoad
    - can be used in any DIS-SYS (App Server, Database Server,....)
    - mostly used in AppServer
    

# Client-Server Protocol: 
    - Simple HTTP 
        'Client ---req--> Server
         Client <---res-- Server'

    - To get realtime updated data
        - AJAX Polling
        - WebSockets
        - Server-Sent Events(SSEs)

# Proxy Server:
    - Open Proxy
    - Revers Proxy
```

## Caching:

{% tabs %}
{% tab title="First Tab" %}


```fsharp
- fasterThanOriginalDataSource, shortTermMemory, limitedSpace
- can store mostRecentlyUsedItems, hotItems, mostRequiredItems, notOftenUpdatingItems


# Application Server Cache:
- Local Machine Cache
    - eachAppServerHasOwnCache
    - Not a goodIdea for DIS-SYS // eachTime LB might sent req to different AS
- Global Cache
    - Use: External System to Store Cache // Redis, Memcache
    - If once cached, all AppServer(AS) can access
    - Distributed Caching // Memcache

## Cache: Invalidation
    '1. Write-Through Cache'
        - writeData: both DB & Cache same time
        - Pros: data-consistency(btwn: cache & DB)
        - Cons: slowWrite
        
    '2. Write-Around Cache'
        - writeData: only in DB (cache will be deleted)
        - Pros: fastWrite
        - Cons: slowRead (firstTime needs to read from DB)
        
    '3. Write-Back Cache'
        - writeData: only in Cache (DB will be updated async)
        - Pros: superFastWrite, bestFor:writeHeavyApp
        - Cons: dataLoss (cacheServerCrash)

## Cache: Eviction Policies
    - 'LRU' (***MOST-PREFERRED***)
        - Least Recently Used: item deleted first 
        - Cons: 
            - sometimes lessFreqUsedItem will replace mostFreqUsedItem
                - since mostFreqUsedItem - not used recently
        
    - LFU // Least Frequently Used: item deleted first
    - FIFO/LIFO
    - RR // Random Replacement


# CDN
    - Static media content (img, videos, html, css, js,...)
    - stored/cached in your nearby ServerZones and read from nearBy ServerZones

```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}



## Database:

{% tabs %}
{% tab title="Summary" %}


```fsharp

# NoSQL vs SQL:

## NoSQL: 
    - 'BASE' (Basically Available, Soft state, Eventually consistent)
     
    - Non-Relational, UnStructured/Semi-Structured, DeNormalized Data
    - No Table Structure (dynamic schema)
    - 'Distributed' -by nature (horizontally scalable) (cheap to scale)
    - can handle huge volume of data (structured/un-structured)
    - cannot gurantee ACID (not suitable where 'consistentcy is must') // e.g. financial transaction
    
    - Scalability: 
        - verically scalable // (costly to scale)
        - horizontally scalable // Natively Distributed // Easy to scale
        
    - NoSQL DB - Types:
        - Key-Value DB // DynamoDB, Redis
        - Document DB  // MongoDB, CouchDB
        - Columnar DB  // Cassandra
        - Graph DB     // Neo4J

## SQL: 
    - Satisfy all 'ACID' Properties // Consistent
        - 'ACID' (Atomicity, Consistency, Isolation & Durability)
        
    - Relational(RDBMS), Structured Data, Normalized Data
    - Table Structure (pre-defined schema)
    
    - Scalability: // Not natively Distributed // not easy to scale
        - verically scalable // (costly to scale)
        - horizontal scaling // Not natively Distributed // not easy to scale
            - 'read-replicas' provides horizontal scaling // but it is limited
            -  Database Partioning
                - Horizontal Partioning (Database Sharding) // splitByRows
                - Vertical Partioning // splitByColumns

        
    - Not Distributed (verically scalable) (costly to scale) (read-replicas provides horizontal scaling)
    - cannot handle huge volume of data
    - 'can gurantee ACID' (consistent & durable) (suitable for financial transaction)


// ---------------------------------------------------------------------------------------------

# How do we scale `SQL` db ?
 // SingleMachine is notScalabale - Distribute them manually 
 - Using 'Read Replicas'
 - Using 'Database Partioning' 
     - // Note: NoSQL dbs are natively distributed



## Distributed Database
- Database Partioning // to handle 'Large Datasets'
    ### Horizontal Partioning (Database Sharding) // Spliting the table horizontally 
        - Split the Table By Row (store some rows of data in diferrent table (diff machine))
        
        # Techniques:
        - Shard by UserId or Location or ...
        - Consistent Hashing
        - Hirerichal Sharding
        
    ### Vertical Partioning // Spliting the table vertically
        - Split the Table By Column (store some colums in diferrent table (diff machine))
        

- Database Replication (Read Replicas) // to 'Read' Fast & Reliability


## Distributed Database Problems:
- Distributed Transactions
- Distributed Locks
- Load Balancing (LB) // uniformlyDistributeLoad
    - Consistent Hashing Ring
- CAP Theorem


// ---------------------------------------------------------------------------------------------


## Database Indexing
- increases 'READ' performance
    - searchFaster: specific column in sortedIndexTable
- decreases 'WRITE' performance
    - if we have multiple indexes on a table,
        - whenever add/update a row data, 
        - that needs to be updated in all the index tables data
```
{% endtab %}

{% tab title="ACID" %}
ACID Transaction&#x20;

A type of database transaction that has four important properties:&#x20;



**Atomicity**: The operations that constitute the transaction will either all succeed or all fail. There is no in-between state. \
Example: both update will succeed or both will fail

```sql
BEGIN TRANSACTION;
UPDATE balances SET balance=balance-100 WHERE username = 'jag';
// updated 1 record
UPDATE balances SET balance=balance+100 WHERE username = 'sundar';
// updated 1 record
COMMIT;
```

**Consistency**: The transaction cannot bring the database to an invalid state. After the transaction is committed or rolled back, the rules for each record will still apply, and all future transactions will see the effect of the transaction. Also named Strong Consistency.&#x20;

**Isolation**: The execution of multiple transactions concurrently will have the same effect as if they had been executed sequentially. \
Example: &#x20;

```sql
// User 1 and User 2 executing the command in parallel 

User1:
------
BEGIN TRANSACTION;
UPDATE balances SET balance=balance-100 WHERE username = 'jag';
// updated 1 record

User2: 
------
BEGIN TRANSACTION;
UPDATE balances SET balance=balance-100 WHERE username = 'jag';
// .....pending..... (will wait until User1 commits the transaction)

User1:
------
COMMIT;


User2: 
------
// .....pending.....
// updated 1 record
COMMIT;

```

**Durability**: Any committed transaction is written to non-volatile storage. It will not be undone by a crash, power loss, or network partition.
{% endtab %}

{% tab title="Details" %}
### Database Indexing:

* [https://www.youtube.com/watch?v=-qNSXK7s7\_w](https://www.youtube.com/watch?v=-qNSXK7s7\_w)
*

### Database Partitioning

* [https://www.youtube.com/watch?v=QA25cMWp9Tk](https://www.youtube.com/watch?v=QA25cMWp9Tk)
*
{% endtab %}
{% endtabs %}





## Concepts:

```fsharp


# Asynchronous Processing
- Messagin Queue
- Event Driven Architecture (Pub/Sub)


# Duplicate Detection
For Smalller Content,
- Hash Table
- Bloom Filter (E.g. WebCrawler find URL duplicate)


# Search File Content:
    - Brute Force
    - Index (Meta Data)
    - Inverted Index 
    
For Larger Content,
- Hashing (MD5) // need exact content to check, can't detect simmilar content check
- SimHash // quickly estimate how similar two largeConents are // Google uses this
- MinHash
- Fuzzy Search
- Latent Semantic Indexing
- Standard Boolean Modal




#Compression Technique:
- Store in Bit Representation





```



## System Design (Example Apps)

```fsharp
# URL shortner:
----------------
shortUrlKey:
- MD5 Hash // but it has longerHash
- Pre-Generated Random Keys // [RECOMMENDED]
    1.  'not-used-keys-table'
    2.  'used-keys-table'
    3.  'buffer-keys-table' (optional) 

# Distributed Web Crawler
--------------------------

URL Reader >> URL Queue >> URL Filter (Invalid, Duplicate) >> Crawl Queue 
>> Crawler:: [DNS Cacher >> Fetcher >> HTML Parser] 
    >> [Content Extracter >> addRequiredContentToDB (Output Queue >> Output Filter (duplicateContentFilter) >> Output Writer]
    >> [URL Extractor >> URL Sanitizer >> URL Queue]
        
    


## Politness / Priority:
- URL Frontier // Priorities, Freshness, Politeness
- Redis (Bull Library) // Concurrency, Priorities, Delayed Jobs, Repeatable Jobs, Rate Limiter


## Repeatable Jobs:
- Cron Job

## Filter Duplicate URLs:
- BloomFilter (firstLevelCheck) + NoSQL DB Lookup



```



Distributed Locks

```fsharp
```
