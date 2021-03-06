# RDBMS

```fsharp
## How do we scale RDBMS db
- Use Read Replicas (One Write Master/ Multiple Read Slaves) (route read queries to slaves)
- Horizontal Scaling
    - We have to logicaly break (one database into multiple databases)
        - Use Hashing: route 'A' customer to one db and 'B' db to another customer
        - Not highly dependent tables can be moved to different db
        - each db can have many Read Replicas

---------------------------------------------------------------------------------

## Joins  // A ___ JOIN B
- 'INNER JOIN' (will get only common records between A table and B table) (no unmatching records) (all A and B columns, duplicate columns will be present)
- 'JOIN' (Natural Join) (will get only common records between A table and B table) (no unmatching records) (no duplicate columns)
- 'LEFT JOIN' (will get all A table records and (A table`s matching ) --B table record (unmatching records dispalyed as NULL)
- 'RIGHT JOIN' (will get all B table records and (B table`s matching) --A table record (unmatching records dispalyed as NULL)


## View / Materialized View 
// Frequently used (joined table) queries can be created as View
    - View: (Logical representaion) (No Phyical Table) (since records are references, we always get updated record)
    - Materialized View: (Phyical Representation) (Joined Table is Created) (to update records, needs triggers)

## Partitioning / Sharding

## Query 3rd Max Salary Record
```

## Read Replicas

* `Master/ Slave: One Write Master/ Multiple Read Slaves` 
  * Write happens only on Master
  * Read happens on Slaves

### Read Replicas- helps RDMBS

* **Improving Performance**
  * Reduce the load on Master -`by routing read queries to slaves`
  * we can increase the no. of instances of Read Replicas
* **High Availability**
  * we can _**promote a read replica**_ if the source/`Master DB instance fails`  
* **Disaster Recovery**
  * we can replicate db instances `across AWS Regions` helps in Disaster Recovery
    * But this functionality complements,
    * the synchronous replication, automatic failure detection, and failover provided with Multi-AZ deployments.

### Why `write` happens only on `Master` why not on slaves?

* AWS does the Read Replicas asynchronously, If we allow write on slaves, there might be situation where `data might not be consistent` across instances
* If we allow that, we violate ACID properties of RDBMS
  * **Data Consistency** is the one of key property 

**Pricing:** Read replicas are billed at the same rates as standard/master DB instances.

### Multi-AZ Deployments vs Read Replicas

| Multi-AZ Deployments | Read Replicas |
| :--- | :--- |
| `Synchronous replication` – highly durable | Asynchronous replication – highly scalable |
| Only database engine on primary instance is active | `All read replicas are accessible` and can be used for read scaling |
| `Automated backups` are taken from standby | No backups configured by default |
| Always span `two Availability Zones` within a single Region | Can be within an Availability Zone, Cross-AZ, or `Cross-Region` |
| Database engine version upgrades happen on primary | Database engine version upgrade is independent from source instance |
| `Automatic failover` to standby when a problem is detected | Can be manually promoted to a standalone database instance |

NoSQL

* Eventually Consistent 

## Joins

Must Read:

{% embed url="http://www.sql-join.com/sql-join-types" caption="" %}

![](../../../.gitbook/assets/image-16.png)

{% embed url="https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/" caption="" %}

## Query 3rd Max Salary Record

{% embed url="https://javarevisited.blogspot.com/2016/01/4-ways-to-find-nth-highest-salary-in.html" caption="" %}

 

