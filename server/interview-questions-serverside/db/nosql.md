# NoSQL

```fsharp
## NoSQL vs SQL
- NoSQL: 
    - 'BASE' (Basically Available, Soft state, Eventually consistent) 
    - No Table Structure (dynamic schema)
    - 'Distributed' -by nature (horizontally scalable) (cheap to scale)
    - can handle huge volume of data (structured/un-structured)
    - cannot gurantee ACID (not suitable where 'consistentcy is must') // e.g. financial transaction
    
- SQL: 
    - 'ACID' (Atomicity, Consistency, Isolation & Durability)
    - Table Structure (pre-defined schema)
    - Not Distributed (verically scalable) (costly to scale) (read-replicas provides horizontal scaling)
    - cannot handle huge volume of data
    - 'can gurantee ACID' (consistent & durable) (suitable for financial transaction)


## NoSQL Types
- Document Based (MongoDB)
- Key-Value Based (Redis)
- Column Based (Cassandra)
- Graph Based (Neo4j)

```

## NoSQL

* NoSQL \(also refers to **Not only SQL**, non-SQL or non-relational\) 
* is a database which gives you a way to `manage the data` which is in a `non-relational form` 

  * \(non-relational form --&gt; not table structured\)

* NoSQL is an alternative to conventional relational databases in which data is put in tables 

  * and the data structure is carefully designed before the database is created.
  * It is mainly helpful for working with `huge sets of distributed data`. 

* NoSQL databases are by default `scalable, high performant and flexible`.
  * It can also deal with a **wide variety of data models**.



## **NoSQL Types**

* **Document Based**
  * `MongoDB`, CouchDB,..
  * \(Stores as document format e.g. JSON\)
* **Key-Value Based**
  * `Redis`, Dynamo, ZooKeeper,..
  * \(Map or Dictionary representation\) 
* **Column Based**
  * `Cassandra`, HBase, Google BigTable,..
  * Wide column stores and arranges the data tables as columns rather than as rows
  * can query a **`large volume of data`** very quickly than the traditional databases
  * timeseries, recommendation engines, catalogs, fraud detection, 
* **Graph Based**
  * `Neo4j`, ArangoDB, Titan,..

\*\*\*\*

## **SQL vs NoSQL**

<table>
  <thead>
    <tr>
      <th style="text-align:left">SQL</th>
      <th style="text-align:left">NoSQL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">SQL databases are mainly relational database (RDBMS).</td>
      <td style="text-align:left">NoSQL databases are mainly non-relational or <code>distributed databases</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">An aged technology.</td>
      <td style="text-align:left">Relatively young technology.</td>
    </tr>
    <tr>
      <td style="text-align:left">SQL databases are <code>table based</code> in the form of row &amp; columns
        and must strictly adhere to standard schema definitions.
        <br />They are a better option for applications which need multi-row transactions.</td>
      <td
      style="text-align:left">
        <p>NoSQL databases can be based on</p>
        <p><code>documents, key-value pairs, columns, graphs</code>
        </p>
        <p>and they don&#x2019;t have to stick to standard schema definitions.</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">They have a well-designed <code>pre-defined schema</code> for structured
        data.</td>
      <td style="text-align:left">They have the <code>dynamic schema</code> for unstructured data. Data can
        be flexibly stored without having a pre-defined structure.</td>
    </tr>
    <tr>
      <td style="text-align:left">SQL databases favors <code>normalized</code> schema.</td>
      <td style="text-align:left">NoSQL databases favors <code>de-normalized</code> schema.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Costly to scale.</code>
      </td>
      <td style="text-align:left"><b><code>Cheaper to scale</code></b> when compared to relational databases.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>SQL databases are <code>vertically scalable</code>.</p>
        <p>They can be scaled by increasing the hardware capacity (CPU, RAM, SSD,
          etc.) on a single server.</p>
      </td>
      <td style="text-align:left">
        <p>NoSQL databases are <code>horizontally scalable</code>.</p>
        <p>They can be scaled by adding more servers to the infrastructure to manage
          large load and lessen the heap.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">They are a good fit for complex queries as SQL has a standard interface
        for handling queries.
        <br />The syntax of SQL queries is fixed.</td>
      <td style="text-align:left">Not a good fit for complex queries as there is no standard interface in
        NoSQL for handling queries.
        <br />The queries in NoSQL are not as powerful as SQL queries.
        <br />It is called as <code>UnQL</code>, and the syntax for using the Unstructured
        query language will vary from syntax to syntax.</td>
    </tr>
    <tr>
      <td style="text-align:left">SQL databases <code>do not suit</code> well for <code>hierarchical data</code> storage.</td>
      <td
      style="text-align:left">NoSQL databases suit best for <code>hierarchical data</code> storage as
        it follows the key-value pair method for storing the data.</td>
    </tr>
    <tr>
      <td style="text-align:left">From a commercial perspective, SQL databases are generally classified
        as open source or closed source.</td>
      <td style="text-align:left">They are classified on the basis of the way they store data as key-value
        store, document store, graph store, column store, and XML store.</td>
    </tr>
    <tr>
      <td style="text-align:left">SQL databases properly follow <code>ACID properties</code> (Atomicity, Consistency,
        Isolation &amp; Durability).</td>
      <td style="text-align:left">
        <p>NoSQL databases properly follow</p>
        <p><code>Brewers CAP theorem</code> 
        </p>
        <p>(Consistency, Availability, and Partition tolerance). <code>Eventually Consistent :) </code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Adding new data in SQL database requires some changes to be made like
        backfilling data, altering schemas.</td>
      <td style="text-align:left">New data can be easily inserted in NoSQL databases as it does not require
        any prior steps.</td>
    </tr>
    <tr>
      <td style="text-align:left">Excellent vendor support and community support is available for all SQL
        databases.</td>
      <td style="text-align:left">Only limited community support is available for NoSQL databases.</td>
    </tr>
    <tr>
      <td style="text-align:left">Best fit for high transaction-based applications.</td>
      <td style="text-align:left">You can use NoSQL for heavy transactional purpose. However, it is not
        the best fit for this.</td>
    </tr>
    <tr>
      <td style="text-align:left">Not suitable for hierarchical data storage.</td>
      <td style="text-align:left">Suitable for hierarchical data storage and storing large data sets (E.g.
        Big Data).</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Example of SQL databases:</p>
        <p>MySQL, Oracle, MS-SQL, SQLite.</p>
      </td>
      <td style="text-align:left">
        <p>Examples of NoSQL databases:</p>
        <p>MongoDB, Redis, Cassandra, Neo4j.</p>
      </td>
    </tr>
  </tbody>
</table>

## Security: SQL Vs NoSQL 

* Database Security is required to provide --&gt; **CIA** \(Confidentiality, Integrity, and Availability\)
  * Confidentiality means that only the authorized users or systems can access the data, 
  * Integrity is the accuracy and consistency of the data over its lifespan 
  * Availability means that the data should be available whenever it is needed.
* Most of the enterprise-based relational databases like Oracle and MSSQL have strong security features integrated into them. 
  * They abide by the ACID properties which ensure secure and reliable database transactions.
* RDBMS also has features like role-based security, access-control via user-level permissions, encrypted messages, support for row and column access control, etc. 
  * However, these security features do need a significant licensing fee and affect the speed of data access.
* For an application which is handling a huge volume of unstructured data, we can’t solely use SQL based databases.
  *  **For Example**, Social networking websites. These applications have two main requirements i.e. scalability and availability. This requirement is served by NoSQL databases.
* However, NoSQL databases security is not as robust as relational databases security. 
  * Unlike SQL databases, the NoSQL databases have `very few inbuilt security features` in order to allow `faster data access`. 
  * They lack confidentiality and integrity attributes. 
  * Also, as they **don’t have** a **fixed** and **well-defined schema,** 
    * you `can’t segregate the permissions`
* Hence, as NoSQL databases don’t provide strong security features at their end, 
  * you will have to **rely** upon ****the **security features of the application** which is accessing the data. 
* NoSQL databases are an easier target for security attack when compared to the relational databases.



NoSQL does not strictly follow ACID properties.

## NoSQL - BASE \(Basically available, soft state, eventually consistent\) 

* **Eventually consistent**
  * `Instead of being` **`consistent after every transaction`**, 
    * it is okay here for the database to be in a consistent state eventually. 
  * It may not be the case that you will always see the current data in NoSQL databases. 
  * You may be seeing the data as per last taken snapshot and a simultaneous transaction can interfere with each other.
  * This `inherent race condition` is a risk that is imposed by NoSQL databases.



## When To Use NoSQL?

**Given below are the use cases where you should prefer using NoSQL databases:**

* To handle a `huge volume of structured, semi-structured and unstructured data.`
* Where there is a need to follow modern software development practices like Agile Scrum and if you need to deliver prototypes or fast applications.
* If you prefer object-oriented programming.
* If your relational database **is not capable enough to scale up** to your traffic at an **acceptable cost**.
* If you want to have an efficient, scale-out architecture 
  * in place of an expensive and monolithic architecture.
* If you have local data transactions that need not be very durable.
* If you are going with schema-less data and want to include new fields without any ceremony.
* When your priority is easy scalability and availability.

## When To Avoid NoSQL?

* `If 'consistency' is a must` and if there aren’t going to be any large-scale changes in terms of the data volume, then going with the SQL database is a better option.
* NoSQL also lacks in the ability to perform dynamic operations. 
  * It `can’t guarantee ACID properties`. 
  * In such cases like **financial transactions**, etc., you may go with SQL databases.
* If you are required to perform complex and dynamic querying and reporting, then you should avoid using NoSQL as it has a limited query functionality. For such requirements, you should prefer SQL only.
* You should also avoid NoSQL if your application needs run-time flexibility.

## Pros And Cons of SQL & NoSQL

### **SQL Pros:**

* It is highly suitable for relational databases.
* Has a predefined schema which is helpful in many cases.
* Normalization can be greatly used here, thus it also helps in removing redundancy and organizing data in a better way.
* Transactions in SQL databases are ACID compliant, thereby guarantees security and stability.
* Follows well-defined standards like ISI and ANSI which are accepted worldwide.
* Code-free.
* Unbeatable speed in retrieving database records with great ease.
* Uses single standardized language i.e SQL across different RDBMS.

### **SQL Cons:**

* The process of interfacing is complex.
* As SQL is an object, it occupies space.
* Handling Big data is very costly as you will have to increase the hardware for scaling.
* When a table is dropped, the view becomes inactive.

### **NoSQL Pros:**

* Capable of handling big data.
* As it is schema-less and table free, it offers a high level of flexibility with data models.
* It is a low-cost database and the open source NoSQL databases provide very affordable solutions to small enterprises.
* Easier and low-cost scalability. You don’t need to increase the hardware for scaling. You just need to add more servers to the pool as NoSQL is schema-free and built on distributed systems.
* Detailed database modeling is not required here. Hence it saves time and effort.

### **NoSQL Cons:**

* The benefits of NoSQL come at the cost of relaxing ACID properties. 
  * NoSQL offers only eventual consistency.
* Relatively less community support.
* Lacks standardization, unlike SQL, which in turn creates some issues during migration.
* Inter-operability is also a concern in the case of NoSQL databases.

#### Conclusion

We learned the difference between SQL vs NoSQL in detail here. The choice of the database will depend upon your preferences, business requirements, volume, and variety of data.

NoSQL databases are gaining large popularity these days due to their capacity to integrate big data, low cost, easy scalability, and open source features. However, it is still a relatively young technology and lacks standardization, unlike SQL. Lack of ACID compliance is also a concern with NoSQL.



{% embed url="https://www.softwaretestinghelp.com/sql-vs-nosql/" %}





