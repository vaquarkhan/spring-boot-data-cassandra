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


- https://bezkoder.com/spring-boot-cassandra-crud
