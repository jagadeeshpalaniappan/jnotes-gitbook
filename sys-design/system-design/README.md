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



# Distributed System Problems:
------------------------------
- Load Balancing     // Soln: Load Balancers
- Handle Failures    // Soln: Circuit Break Patterns, Bulkhead Pattern
- Security (Authentication/Authorization) // Soln: API Gateway
- Rate Limiting      // Soln: API Gateway

Microservices:
- Service Discovery  // Soln: API Gateway
- Deployment // Soln: CI/CD, Jenins
- Debugging/Logging/Tracing // Soln: API Gateway(traceId), Splunk
- Monitoring // Son: Newrelic, AppDynamics



# Event Driven Architecture (Pub/Sub)
------------------------------
    - FaaS // Function as a Service // AWS Lamda, Google Cloud Fn,..
    - Apache Kafka



# Distributed File System 
# Distributed Data Processing
------------------------------
    1. GFS / Hadoop (HDFS) & Run 'MapReduce'
    


# API Gateway:
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

## AppServer\(AS\):

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
    - stored/cached in your nearby Server Zones

```

## Database:

```fsharp
#SQL vs NoSQL
- SQL: 
    - Relational(RDBMS), Structured, Normalized Data
    - Satisfy ACID Properties // Consistent
    - Difficult to Scale // Manually implement Distributed System
    
- NoSQL: 
    - Non-Relational, UnStructured/Semi-Structured, DeNormalized Data
    - Does NOT Satisfy ACID Properties // Eventually Consistent
    - Easy to Scale // Natively Distributed System
    - Types:
        - Key-Value DB // DynamoDB, Redis
        - Document DB  // MongoDB, CouchDB
        - Columnar DB  // Cassandra
        - Graph DB     // Neo4J

## Database Indexing
- increases 'READ' performance
    - searchFaster: specific column in sortedIndexTable
- decreases 'WRITE' performance
    - if we have multiple indexes on a table,
        - whenever add/update a row data, 
        - that needs to be updated in all the index tables data


## Distributed Database
- Database Partioning // to handle 'Large Datasets'
    - Horizontal (Database Sharding)
        - Shard by UserId or Location or ...
        - Consistent Hashing
        - Hirerichal Sharding
    - Vertical

- Datbase Replication (Read Replicas) // to 'Read' Fast & Reliability


## Distributed Database Problems:
- Load Balancing (LB) // uniformlyDistributeLoad
- Consistent Hashing Ring
- CAP Theorem
- Distributed Transactions
- Distributed Locks
```

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



## System Design \(Example Apps\)

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



