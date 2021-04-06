### Data Types

Scalar
- number: could also represent datetime in epoch time(from 1970)
- string: could also represent datetime using ISO 8601 format, **cannot be empty**
- binary: encode binary in `base64` before inserting into dynamodb
- null

Document: can be nested up to 32 levels deep
- list: ["cookies", "coffee", 3.1415], can be empty
- map: just like a `json` object, can be empty


Set: multiple scalar values of the same type: string set, number set, binary set. 
- each value must be unique
- **cannot be empty**


### Summary
- You have to provide a value for each attribute, otherwise just don't add this attribute for current item.
