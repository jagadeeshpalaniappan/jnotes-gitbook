# System Design

System Design

```bash
# Single Machine Fails:
Pros:
    - Simple Architecture
Cons:
    - SPOF: Single Point Of Failure
    - Cannot 'Scale' // Scaling is Limited
    

# Need Multiple Machines: (Distributed System)
Pros:
    - Can 'Scale' without any limits
Cons:
    - Complex Architecture
    
# Distributed System:
- Load Balancing // UniformlyDistributeLoad

- Consistent Hashing Ring
    
- Distributed Transactions
- Distributed Caching

- Database:
    - SQL vs NoSQL
    - Database Partioning
        - Horizontal (Database Sharding)
            - Shard by UserId or Location or ...
            - Consistent Hashing
            - Hirerichal Sharding
        - Vertical
    - Datbase Replication (Read Replicas)


```

