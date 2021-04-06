## Secondary Index
Secondary Indexes are used to facilitate various access patterns

- contains a subset of attributes, along with an `alternate key` to support query operations.
- One table can have `multiple` secondary indexes.


### Global Secondary Index (`GSI`)

> create a secondary index is just like create another table with the same data as the base table and have different primary key.

Index with a different `partition` and `sort` key from those on the base table. The primary key of a GSI can be either a partition key or a combination of a partition key and a sort key.


### Local Secondary Index (`LSI`)

Index with the same partition key as it in the base table, but have a different sort key. The primary key of the LSI must be compose (one partition key and one sort key) and **it must be create at the time of table creation**.


### Features and Limitations

`GSI`:

- it's global because queries on the index span on `all` data in the base table, across `all` partitions (**similar to creating another table and new partition**)
- no size limitations
- has its own RCU/WCU settings separate from the base table.
- **for eventually consistent queries only**



`LSI`:
- it's local because each partition is scoped to ba base table partition with the same partition key. (**In the same table**)
- **Total size per partition key can't exceed 10GB**
- Shares provisioned throughput settings with its base table.
- **Strongly or eventually consistent queries.**


### Summary
- In general, use GSI rather than LSI unless you need **strong consistency** in query result.