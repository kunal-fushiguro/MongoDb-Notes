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
