# MongoDB $inc operator error: Incorrect type for increment value
This example demonstrates an incorrect usage of the `$inc` operator in a MongoDB update query. The `$inc` operator is used to increment or decrement a numeric field. The value passed to `$inc` must be a number. In this example, the value passed is a string, which results in an incorrect update operation.

## Bug
The bug is in the line:
```javascript
db.collection('myCollection').updateOne({ _id: 1 }, { $inc: { count: '1' } });
```
The `count` field is incremented by the string '1', rather than the number 1.  This may cause unexpected behavior, depending on the server version and data type of the `count` field.

## Solution
The solution is to pass a number to the `$inc` operator:
```javascript
db.collection('myCollection').updateOne({ _id: 1 }, { $inc: { count: 1 } });
```
This will correctly increment the `count` field by 1.