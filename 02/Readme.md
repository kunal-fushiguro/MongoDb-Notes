# Cursor

A pointer or iterator that allows an application to retrieve and manipulate data from a collection of documents in a controlled and efficient manner.

### Automatic iteration

Cursors automatically iterate by default, but you can also iterate them manually.

### Batch fetching

Cursors fetch documents in batches to reduce memory consumption and network bandwidth usage.

### Controlled access

Cursors allow you to hold only a subset of database results in memory at a given time.

## Cursor Method

### Count()

- Count the length of data(documents) or Counts the number of documents referenced by a cursor. .

  ```
      db.collection_name.find({key:{$eq:value}}).count()
  ```

### Limit()

- show limited data(documents) or used to specify the maximum number of documents the cursor will return..

  ```
      db.collection_name.find({key:{$eq:value}}).limit(5)
  ```

### Skip()

- Used to skip a specified number of documents in a query result.

  ```
      db.collection_name.find({key:{$eq:value}}).limit(5).skip(2)
  ```

### Sort()

- Used to sort document's result into ascending order (1) or descending order (-1).

  - Ascending order

    ```
       db.collection_name.find({key:{$eq:value}}).limit(5).sort({key:1})
    ```

  - Descending order

    ```
       db.collection_name.find({key:{$eq:value}}).limit(5).sort({key:-1})
    ```

# Logical Operators

Logical operators return data based on expressions that evaluate to true or false.

### $and operator

- Return a data(documents) that match both expressions(conditions).

```
db.collection_name.find({$and:[{"key":{$eq:"value"}},{"key":"value"}]})
```

or

```
db.collection_name.find({"key":{$eq:"value"},"key":"value"})
```

### $or operator

- Return a data(documents) that match any one of the given expressions(conditions).

```
db.collection_name.find({$or:[{"key":{$eq:"value"}},{"key":"value"}]})
```

### $nor operator

- Return a data(documents) that does not match any one of the given expressions(conditions).

```
db.collection_name.find({$nor:[{"key":{$eq:"value"}},{"key":"value"}]})
```

### $not operator

- return a data(document) that not match the given expression(conditon).

```
db.collection_name.find({"key":{$not:{$eq:"value"}}})
```

## Expr Operator

- It allows you to use aggregation expressions within the query language.
- This is particularly useful for comparing fields within the same document.
- The `$expr` operator can be used to perform comparisons, calculations, and other operations that were previously only possible within the aggregation pipeline.

- Consider a collection named `products` with documents that look like this :

  ```
  {
    "_id": 1,
    "name": "Product A",
    "price": 100,
    "discountedPrice": 80
  },
  {
    "_id": 2,
    "name": "Product B",
    "price": 200,
    "discountedPrice": 220
  },
  {
    "_id": 3,
    "name": "Product C",
    "price": 150,
    "discountedPrice": 150
  }
  ```

- Now if you want to find all products where the `discountedPrice is less than the price`, you can use the `$expr` operator like this:

  ```
  db.products.find({
    "$expr": {
      "$lt": ["$discountedPrice", "$price"]
    }
  })
  ```

# Element Operator

### $exists

- It is used to query documents that either contain or do not contain a specified field.</br> basic syntax `{ <field>: { $exists: <boolean> } }`.

  ```
  db.users.find({ "email": { "$exists": true } })
  ```

### $type

- It filters document based on the BSON data type of a field.
  </br> basic syntax `{ field: { $type: "<bson-data-type>" } }`

  ```
    db.users.fint({"email" : {"$type" : "string"} }).count()
  ```

### $size

- It matches documents where the size of an array field matches a specified value.
  </br> basic syntax `{ <arrayField>: { $size: <number> } }`

  ```
  db.orders.find({ "items": { "$size": 2 } })
  ```

# Projection

- the process of selecting specific fields to include or exclude in the documents returned by a query

- This allows you to control which parts of the document you want to retrieve, making your queries more efficient by reducing the amount of data transferred over the network

- Consider a collection named users with documents like these:

  ```
  {
    "_id": 1,
    "name": "Alice",
    "age": 25,
    "email": "alice@example.com"
  },
  {
    "_id": 2,
    "name": "Bob",
    "age": 30,
    "email": "bob@example.com"
  },
  {
    "_id": 3,
    "name": "Charlie",
    "age": 35,
    "email": "charlie@example.com"
  }

  ```

- To find all users and include only the name and email fields, you can use the following query:

  ```
   db.users.find({}, { "name": 1, "email": 1 })
  ```

- To find all users and exclude the age field, you can use the following query:

  ```
   db.users.find({}, { "age": 0 })
  ```
