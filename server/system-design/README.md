# System Design

```fsharp
# System Design
- AppServer(AS):
- Caching
- Database

```

## Distributed System:

```fsharp
# Single Machine Server:
Pros:
    - Simple Architecture
Cons:
    - SPOF: Single Point Of Failure
    - Cannot 'Scale' // Vertical Scaling is Limited
        - Cannot handle huge request
        - Cannot handle large datasets
    

# Distributed System: // Multiple Machine Server
Pros:
    - Can 'Scale' without any limits
Cons:
    - Complex Architecture

```

## AppServer\(AS\):

```fsharp
# Load Balancing (LB) // uniformlyDistributeLoad
    - can be used in any DIS-SYS
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
    '
    - LRU // Least Recently Used: item deleted first
    - LFU // Least Frequently Used: item deleted first
    - FIFO/LIFO
    - RR // Random Replacement
    '


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
```

## Others

```fsharp
- Bloom Filter
```

