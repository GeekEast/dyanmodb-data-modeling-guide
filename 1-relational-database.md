## Relational database

### Good
- **Storage Optimized**: Relational Databases were created to **decrease** the **storage** pressure. Data was **normalized** to save space and cost.
- **Strict Consistency**: Data is **highly structured** ad **normalized**. One piece of data is only saved in one place.

### Bad
- Data is **strictly structured** and maintain and change data structure can be painful.
- Relational Database is not good at dealing with **sparse** data. Sparse data also waste space and cost. 
- **Scale Vertically**: can only be vertically scalable. Although storage is cheap, cpu can be very expensive.


### Use Case
- **data size** is clear before development.
- **data structure** is clear and stable.
- data is **compact** with less sparse data.

In summary, RMDBS is suitable for **size-predictable**, **structure-predictable** and **cheap-storage** decision. And it's not suitable for data whose data size and data structure is consistently **changing** along the its whole lifecycle. 
