### Items and Attributes

- Max Item Size: 400KB
- Recommended Item Size: less than 1KB
- Question: where to see the size?


Operations:

- `PutItem`: replace existing one item
- `UpdateItem`: modify existing one item attributes
- Both operations consume `WCU`, size is calculates of the large of the old and new items.

- `DeleteItem`: delete existing one item. it consumed the WCU based on the size of the deleted item (1 WCU if the item does not exist)


### Primary Key

Two modes:
- only one partition key, must be unique
- one partition key and one sort key, combined as unique, partition key could be the same in this mode.
