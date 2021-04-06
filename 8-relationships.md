
## Relationships in DynamoDB Data Modeling

### One-To-Many Relationships

<p align="center"><img style="display: block; width: 600px; margin: 0 auto;" src=img/2021-04-04-11-19-06.png alt="no image found"></p>

**Access Patterns:**
- get Item by `itemId`  (✅ by `GSI`)
- get Order by `orderId` (✅)
- get items by `orderId` (✅)
- get order by `itemId` (❌ - `2` requests by `GSI`)
- get order by `customerId` (✅ by `GSI`)

<p align="center"><img style="display: block; width: 600px; margin: 0 auto;" src=img/2021-04-04-12-52-50.png alt="no image found"></p>

**GSI:**
- SK,PK
- customerID

### Many-To-Many Relationships

<p align="center"><img style="display: block; width: 600px; margin: 0 auto;" src=img/2021-04-04-11-17-01.png alt="no image found"></p>

**Access Patterns:**
- get project by `projectId` (✅)
- get employee by `employeeId` (✅)
- get projects by `employeeId` (❌ - `2` requests by `GSI`)
- get employees by `projectId` (❌ - `2` requests by `GSI`)
- get projects by `email` (❌ - `2` requests by `GSI`)
- get open projects by `employeeID` (❌ - `3` requests by `3 GSI`)
- get date when James join Project `idp` (❌ - `2` requests by `2 GSI`)

<p align="center"><img style="display: block; width: 600px; margin: 0 auto;" src=img/2021-04-04-23-25-56.png alt="no image found"></p>

### Hierarchy Relationship

<p align="center"><img style="display: block; width: 600px; margin: 0 auto;" src=img/2021-04-05-11-09-36.png alt="no image found"></p>

**Access Patterns:**
- get all state stores within one specific country. (✅)
- get all city stores within one specific state within one specific country. (✅ + `1 GSI`)
- get all postcode stores within one specific city within one specific state and within one specific country.(✅ + `1 GSI`)

**Approach:**
- **PartitionKey**: `country`
- **SortKey**: `stateId#cityId#postcode`