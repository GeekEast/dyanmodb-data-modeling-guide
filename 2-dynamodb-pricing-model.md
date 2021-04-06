## DynamoDB Capacity Modes

### On-Demand (无最低消费)
- pay per request
- automatically scales your capacity up or down
- good for new tables with unknown or unpredictable workloads 
<!-- - TODO: suitable for product -->

request unit:

| Number of Request | Type                       | Size  | Number of RU |
| ----------------- | -------------------------- | ----- | ------------ |
| 1                 | Strongly Consistent Read   | <=4KB | 1            |
| 1                 | Eventually Consistent Read | <=4KB | 1.5          |
| 1                 | Transactional  Read        | <=4KB | 2            |
| 1                 | Standard Write             | <=1KB | 1            |
| 1                 | Transactional  Write       | <=1KB | 2            |


usage:
- no minimum capacity; pay more per request than provisioned capacity
- Idle table not charged for read/write, but only for storage and backups
- No capacity planning required - just make API calls
- Eliminates the tradeoffs of over - or under-provisioning
- **Use on-demand for new product launches**
- **Switch to provisioned once a steady state is reached**

[example](https://calculator.s3.amazonaws.com/index.html)


### Provisioned (有最低消费)
- pay per capacity unit
- specify reads and writes per capacity hour
- auto-scaling
<!-- - TODO: suitable for qa and sandbox env -->


request unit:

| Number of Request | Type                                   | Size  | Number of CU |
| ----------------- | -------------------------------------- | ----- | ------------ |
| 1                 | Strongly Consistent Read  per second   | <=4KB | 1            |
| 1                 | Eventually Consistent Read  per second | <=4KB | 0.5          |
| 1                 | Transactional  Read  per second        | <=4KB | 2            |
| 1                 | Standard Write  per second             | <=1KB | 1            |
| 1                 | Transactional  Write per second        | <=1KB | 3            |


usage:
- **minimum capacity required**
- able to set a budget (maximum capacity)
- but when it reach the maximum capacity, it will experience throttling
- can be auto scaled
- risk of under-provisioning that cost your more than actual usage
- **lower price per API call**


[example: provisioned is 33 times cheaper than on-demand mode](https://calculator.s3.amazonaws.com/index.html)


### Summary
- use on-demand first
- when workload reach steady, transfer to provisioned mode to save a lot of money



