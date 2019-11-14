# DB- Read Replicas

```cpp
# Read Replica: (One Master/ Multiple Slaves) (Write happens on Master)
------------------------------------------------------------------------
# Performance
- Reduce the load on Master -by routing read queries to slaves
- Amazon RDS (MySQL) allows you to add table indexes directly 
    - (without those indexes being present on the master)

#High Availability
- You can promote a read replica if the source/Master DB instance fails

#Disaster Recovery
- You can also replicate DB instances 'across AWS Regions'
- This functionality complements the synchronous replication, automatic failure detection, and failover provided with Multi-AZ deployments


- Asynchronous replication – highly scalable
- Can be manually promoted to a standalone database instance

```

## Why do we need Read Replicas?

**Enhanced Performance**

* You can **reduce the load** on your **source DB** instance --by routing read queries from your applications to the read replica. 
* Read replicas allow you to elastically scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads.
* To further maximize read performance, Amazon RDS for MySQL allows you to add **table indexes directly** to Read Replicas, --without those indexes being present on the master.
* Because read replicas can be promoted to master status, they are useful as part of a sharding implementation. 
  * To shard your database, add a read replica and promote it to master status, then, from each of the resulting DB Instances, delete the data that belongs to the other shard.
  * Because the Amazon RDS for MySQL engine also allows you to perform table-wide actions like adding indexes or new columns to read replicas, you can use its replica-promotion capability to minimize the impact of these actions. 
  * You would direct the DDL for the action to a read replica, promote that read replica to master status, and then redirect database traffic to the new master.

  
**Increased Availability**

* You can promote a read replica if the source DB instance fails. 
* You can also replicate DB instances across AWS Regions as part of your disaster recovery strategy. 
* This functionality complements the synchronous replication, automatic failure detection, and failover provided with Multi-AZ deployments.

  
**Designed for Security**

* **Read replicas also as secured as the main instance**

  
**Pricing**

* Read replicas are billed at the same rates as standard DB instances.

{% embed url="https://aws.amazon.com/rds/details/read-replicas/" %}

