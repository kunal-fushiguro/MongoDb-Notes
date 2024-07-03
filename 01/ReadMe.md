# Managing datbases in mongodb

Before Starting please make sure that you have installed `mongodb` & `mongodb shell` in your computer. </br>

- To check version of mongodb run below command on your terminal :

```
    mongod --version
```

- To check mongodb shell is installed, run below command on your terminal :

```
    mongosh
```

### What is `database` in mongodb ?

- In MongoDB, a database is a collection of documents.

### What is `collections` in mongodb ?

- A collection is a group of related documents that share a common structure. Each document has one or more fields, which are similar to columns in a relational database table.

### What is `documents` in mongodb ?

- Documents are similar to rows in a relational database, but instead of being organized into tables, they are grouped into collections.

## Command's

First Open terminal and run command `mongosh`

### Database related command's

- to check present database or show databses

  ```
  show dbs
  ```

  or

  ```
  show databses
  ```

- to create database

  ```
    use databasename
  ```

  you will not see database in cmd line until we create a atleast one collection.</br>
  and `use` is also used to switch between and select a database. Example :

  ```
  use newdatabasename
  use databasename
  use newdatabasename
  ```

- to delete database

  ```
    use databasename
  ```

  and then

  ```
    db.dropDatabase()
  ```

### Collections related command's

- to create collections

  - first select database

    ```
    use databasename
    ```

  - and then create database using `db.createCollection('<collection-name>’);`
    ```
    db.createCollection("collectionname")
    ```

- to show collections

  ```
  show collections
  ```

- to delete collection
  ```
  db.collectionname.drop()
  ```

### Documents related command's

- Inserting Documents in collection

  - One document insert

    ```
    db.collectionname.insertOne({
        "key":"value",
        "key1":"value2",
        "key3":{
            "key1":"value1"
            "key2":"value2"
        },
    })
    ```

  - Multiple document's insert

    ```
    db.collectionname.insertMany([
        {
            "key1":"value1"
        },
        {
            "key2":"value2"
        },
        {
            "key3":"value3",
            "key4":{
                "key1":"value1"
                "key2":"value2"
            }
        },
    ])
    ```

- to show document's

  ```
  db.collectionname.find()
  ```

- Ordered insert

  - When you perform ordered inserts, MongoDB inserts the documents in the order you provide them. If an error occurs during the insertion of a document, MongoDB stops the process and does not insert any subsequent documents. Example :

    ```
     db.collectionname.insertMany([
        {
            _id:1
            "key1":"value1"
        },
        {
            _id:1               // here the error will occurs and it will only upload
            "key2":"value2"     // first One and stop the process
        },
        {
            "key3":"value3",
            "key4":{
                "key1":"value1"
                "key2":"value2"
            }
        },
    ])
    ```

- Unordered insert

  - When you perform unordered inserts, MongoDB attempts to insert all documents independently. If an error occurs with one document, MongoDB continues to insert the remaining documents. Example :

    ```
    db.collectionname.insertMany([
        {
            _id:1
            "key1":"value1"
        },
        {
            _id:1               // here the error will occurs it will upload
            "key2":"value2"     // all the data except the error one
        },
        {
            "key3":"value3",
            "key4":{
                "key1":"value1"
                "key2":"value2"
            }
        },
    ],{ ordered:false })
    ```

- To find document

  - To find multiple document with exact key value
    ```
        db.collectionname.find({"key1":"value1"})
    ```
  - To find first document with excat key value
    ```
        db.collectionname.findOne({"key1":"value1"})
    ```

### Importing JSON in MongoDB

- To import JSON file data into document use `mongoimport jsonfile_Path.json –d database_name –c collection_name`

  ```
    mongoimport JSON_Products.json -d shop -c products
  ```

- To import JSON_ARRAY file data into document use `mongoimport jsonfile_Path.json –d database_name –c collection_name --jsonArray`

  ```
    mongoimport JSON_Products.json -d shop -c products --jsonArray
  ```

### Exporting JSON in MongoDB

- To export document into JSON file `mongoexport -d Database_name -c collection_name -o file_path.json`

  ```
    mongoexport -d shop -c products -o jsonTest.json
  ```
