# System Design

```fsharp
# System Design
- AppServer(AS):
- Caching
- Database

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

## Misc

```fsharp
- Bloom Filter
- Rate Limiting

```

