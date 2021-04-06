## Partition Key


Data is partitioned based on the `hash` value on its `partition Key`

### Distributed Capacity

When you define your RCU or WCU, they are distributed on each partition. For example:

- You have 500 RCU in total
- You have 2 partitions

So each partition got 250 RCU

> But what if most of the time, only one partition is hit?

This waste the other partition and when Read Request is more than the defined RCU? It will cause `throttling` that dynamodb will start to **refuse** request on the `hot` partition.

**Solution 1: Adaptive Capacity**

Now dynamodb has native Adaptive Capacity supported than the capacity is dynamically distributed among partitions rather than evenly distributed. 

> But each partition in DynamoDB has up to 3000 RCU and 1000 WCU. What if the request is more than those threshold value?

**Solution 2: DynamoDB DAX**

DynamoDB has DAX in-memory caching mechanism to prevent throttling in this case. But DAX is separately charged.

### Ideal Scaling Conditions
- `partition key` is from a high `cardinality` set which means you want `a large number of distinct` values of the partition key.
- Requests are evenly spread over the key space. (prevent the `Hot Key` problem)
- Request are evenly spread over time