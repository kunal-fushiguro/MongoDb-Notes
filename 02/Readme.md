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
