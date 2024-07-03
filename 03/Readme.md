# Update Operations

### updateOne()

- Used to update signle document using `$set`.

  - basic syntax `db.collectionName.updateOne({ filter },{ $set: {existingField: newValue, newField: "new value", // ... }, });`

    ```
        db.users.updateOne(
            { "name" : "kunal" },
            { $set: { "salary" : "1000000" } }
        )
    ```

  - We can also use `$set` to add new field same the way we update a field.

### updateMany()

- used to update multiple document `$set`.

  - basic syntax `db.collectionName.updateMany({ filter },{ $set: { existingField: newValue, // ... }, });`

    ```
     db.products.updateMany(
           { "price" : 1200 },
           { $set: { "discount" : "30%" } }
       )
    ```

### $unset

- Used to remove field

  - basic syntax `db.collectionName.updateOne( { filter }, { $unset: { fieldName: 1 } } )`

    ```
     db.users.updateOne(
      {
        "isOnline": false
      },
      {
        $unset : { "isOnline" : 1 }
      }
     )
    ```

### $rename

- Used to rename field

  - basic syntax `db.collectionName.updateOne({ filter },{ $rename: { oldFieldName: "newFieldName" } })`

    ```
      db.users.find(
        {
          "age": { $gt : 18 }
        },
        {
          $rename : { "name" : "fullName" }
        }
      )
    ```

# Updating arrays and Embedded Documents

### $push

- Used to add new field in Embedded Documents.

  - basic syntax `db.collectionName.updateOne({ filter }, { $push: { arrayField: new element" } });`
    ```
      db.videos.updateOne(
        {
          "name":"codewithharry"
        },
        {
          $push : {
            "comments" : {
              "user" : "kunal",
              "text" : "hello harry bhai"
            }
          }
        }
      )
    ```

### $pop

- Used to pop the Embedded Documents.

  - basic syntax `db.collectionName.updateOne( { filter }, { $pop: { arrayField: value } });`

    ```
      db.videos.find(
        {
          "name" : "codewithharry"
        },
        {
          $pop : {
            "comments" : 1
          }
        }
      )
    ```

# Delete Operations

### deleteOne()

- Used to delete one document.

  - basic syntax `db.collectionName.deleteOne({"fieldName" : "Value"})`

    ```
    db.videos.deleteOne(
      {
        "_id" : "ad2e12d1212e12e"
      }
    )
    ```

### deleteMany()

- Used to delete many documents.

  - basic syntax `db.collectionName.deleteMany({"fieldName" : "Value"})`

    ```
    db.products.deleteMany(
      {
        "order" : "sold"
      }
    )
    ```
