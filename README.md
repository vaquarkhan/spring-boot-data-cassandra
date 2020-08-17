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




--------------------------------------------




- https://bezkoder.com/spring-boot-cassandra-crud
- https://stackoverflow.com/questions/31513225/connecting-to-multi-node-cassandra-cluster-using-spring-data-cassandra

