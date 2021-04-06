
## DynamoDB Data Modeling

### Steps
- start with an `ERD`
- define the `access patterns` (how the database is accessed)
- define the `primary key` and `secondary indexes`.

## NoSQL Data Modeling Concepts

NoSQL was born for scalability. When you do the data modeling for DynamoDB, you also should consider the scalability. Which means

> You should design table to optimize for your application's `access pattern`.

**Identity Access Pattern Approaches**
- new apps: review `user stories` and analyze the candidate access patterns.
- Existing apps: analyze `logs`

**Access Pattern Examples**

- find employee by ID
- get all items for a given order ID
- get all employees with a given job title
- get total product inventory


**Principles**

Optimize for the **most common** queries' `speed` and `cost`

- each access pattern only require only `1` single request
- use as few tables as possible - preferably **a single table** (schemaless allows you do this)

> when you have several tables, 
> - you need to use the transactional apis, you might 
> - trigger multiple api requests to dynamodb - the N+1 problem, 
> - high latency to the end users.
> - more complexity per query - "fake joins" across dynamodb table
> - higher cost RCU/WCU