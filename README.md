# Spring Boot Cassandra CRUD example - Restful CRUD API

For more detail, please visit:
> [Spring Boot Cassandra CRUD example using Spring Data](https://bezkoder.com/spring-boot-cassandra-crud/)

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
