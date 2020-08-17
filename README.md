# Spring Boot Cassandra CRUD example - Restful CRUD API


## Run Spring Boot application
```
mvn spring-boot:run
```

-----------------------------------------

### Create table

         CREATE TABLE tutorial (
              id UUID PRIMARY KEY, 
              title text,
              description text,
              published Boolean
            );

            SELECT * FROM edlapi.tutorial ;
            
            
            
            
### create data into table 

POST
 
            http://localhost:8080/api/tutorials
            
            {
             "title":"test1",
              "description":"this is test cassabdra call"
             }

### multi cluster configuration

- https://stackoverflow.com/questions/52123266/spring-boot-2-cassandra-multiple-keyspaces-or-clusters

We can pass a comma separated list of contact points. It is not strictly required, but recommended though.

### Additional info

Giving a single node as a contact point is sufficient for any driver. The driver will then automatically identify the entire cluster with the help of topology defined.

### But there is a catch

what if that one node is down? So I usually provide couple of nodes to my DataStax driver. (At least one node per rack in a single cluster). Some people provide seed nodes as contact points. This option is also recommended.

### Seed Nodes vs Contact Points

Its important to keep in mind the purpose of 'Seed Nodes' and 'Contact Points'. Seed Nodes supports node and topology discovery when the Cassandra Cluster starts up. 'Contact Points' are used by drivers when interacting with the Cassandra Cluster.

Please also refer to your driver's documentation and pay attention to the default topology setting your driver has.



###  DCAwareRoundRobinPolicy

A data-center aware Round-robin load balancing policy.
This policy provides round-robin queries over the node of the local data center. It also includes in the query plans returned a configurable number of hosts in the remote data centers, but those are always tried after the local nodes. In other words, this policy guarantees that no host in a remote data center will be queried unless no host in the local data center can be reached.

If used with a single data center, this policy is equivalent to the LoadBalancingPolicy.RoundRobin policy, but its DC awareness incurs a slight overhead so the LoadBalancingPolicy.RoundRobin policy could be preferred to this policy in that case.



--------------------------------------------

### Hbase Vs Cassandra

 ![Alt Text](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcS3pMZBImzqGSCeJV3-9ffwu2B156bBNv1_dw&usqp=CAU ) 

- https://www.scnsoft.com/blog/cassandra-vs-hbase
- https://www.scitepress.org/Papers/2017/64388/64388.pdf
- https://www.iflexion.com/blog/hbase-vs-cassandra

### HBase and Cassandra Comparison Table

|--------------------------------|:-------------------------------------------------------------------------:|:--------------------------------------------------------|
| Points                         |                                   HBase                                   |                    Cassandra                            |
|--------------------------------|:-------------------------------------------------------------------------:|:--------------------------------------------------------|
| CAP Theorem                    | Consistency & Availability                                                | Availability and Partition Tolerance                    |
|--------------------------------|:-------------------------------------------------------------------------:|:--------------------------------------------------------|
| Coprocessor                    | Yes                                                                       | No                                                      |
|--------------------------------|:-------------------------------------------------------------------------:|:--------------------------------------------------------|
| Rebalancing                    | HBase provides Automatic rebalancing within a cluster.                    | Cassandra also provides rebalancing but not for overall cluster |
|--------------------------------|:-------------------------------------------------------------------------:|:---------------------------------------------------------|
| Architecture Model             | It is based on Master-Slave Architecture Model                            | Cassandra is based on Active-Active Node Modal           |
|--------------------------------|:-------------------------------------------------------------------------:|:---------------------------------------------------------|
| Base of Database               | It is based on Google BigTable                                            | Cassandra is based on Amazon DynamoDB                    |
|--------------------------------|:-------------------------------------------------------------------------:|:---------------------------------------------------------|
| SPoF (Single Point of Failure) | If Master Node is not available the entire cluster will not be accessible | All nodes having the same role within-cluster so no SPoF |
|--------------------------------|:-------------------------------------------------------------------------:|:---------------------------------------------------------|
| DR (Disaster Recovery)         | DR is possible if Two Master Nodes are configured.                        | Yes, as all nodes having the same role                   |
|--------------------------------|:-------------------------------------------------------------------------:|:---------------------------------------------------------|
| HDFS Compatibility             | Yes, As HBase stores all meta-data in HDFS                                | No                                                       |
|--------------------------------|:-------------------------------------------------------------------------:|:---------------------------------------------------------|
| Consistency                    | Strong                                                                    | Not Strong as HBase                                      |
|--------------------------------|:-------------------------------------------------------------------------:|:---------------------------------------------------------|




-------------------------------------------------


- https://bezkoder.com/spring-boot-cassandra-crud
- https://stackoverflow.com/questions/31513225/connecting-to-multi-node-cassandra-cluster-using-spring-data-cassandra
- https://cassandra.apache.org/doc/latest/getting_started/index.html
- https://docs.spring.io/spring-data/cassandra/docs/current/reference/html/#reference
- https://github.com/spring-projects/spring-data-examples
- https://docs.datastax.com/en/drivers/java/2.2/com/datastax/driver/core/policies/DCAwareRoundRobinPolicy.html
- https://dzone.com/articles/bigtable-model-cassandra-and
- https://medium.com/jorgeacetozi/cassandra-architecture-and-write-path-anatomy-51e339bcfe0c
