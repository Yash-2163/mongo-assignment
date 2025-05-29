# MongoDB Operations – CompanyDB

## Switching to the Database

```js
use CompanyDB
// Output: switched to db CompanyDB
```

## Insert Operations

Insert a few employees into the collection:

```js
db.employees.insertOne({
  name: "Alice Johnson",
  position: "Software Engineer",
  hireDate: ISODate("2024-07-15")
});
// Output: acknowledged, with an insertedId
```

```js
db.employees.insertOne({
  name: "Bob Smith",
  position: "Graphic Designer",
  hireDate: ISODate("2025-01-19") // corrected date
});
// Output: acknowledged, with an insertedId
```

## Query Operations

Find all employees:

```js
db.employees.find();
// Output: documents for Alice Johnson and Bob Smith
```

Find by position:

```js
db.employees.find({ position: "Software Engineer" });
// Output: Alice Johnson's document
```

Find one by name:

```js
db.employees.findOne({ name: "Bob Smith" });
// Output: Bob Smith's document
```

Sort by hire date:

```js
db.employees.find().sort({ hireDate: 1 });
// Output: sorted list from earliest to latest hireDate
```

## Update Operations

Update Bob's position:

```js
db.employees.updateOne(
  { name: "Bob Smith" },
  { $set: { position: "Senior Designer" } }
);
// Output: 1 document modified
```

Add department to software engineers:

```js
db.employees.updateMany(
  { position: "Software Engineer" },
  { $set: { department: "Engineering" } }
);
// Output: matched and modified count shown
```

Set Alice's department:

```js
db.employees.updateOne(
  { name: "Alice Johnson" },
  { $set: { department: "Engineering" } }
);
// Output: 1 document modified
```

## Delete Operations

Delete Alice from the collection:

```js
db.employees.deleteOne({ name: "Alice Johnson" });
// Output: 1 document deleted
```

Optional: Drop the entire employees collection:

```js
db.employees.drop();
// Output: true
```
