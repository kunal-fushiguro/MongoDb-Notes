# Mongodb

### What is `Mongodb` ?

`Mongodb` is an open source, document oriented NoSql database management system.

### What is document database (document oriented) ?

A database that stores information in documents(JSON).

### Why `Mongodb` ?

It is designed for flexibility, scalability, and performance in handling unstructured or semi structured data.

### Comparing SQL and NoSql database

| SQL                                                                            | MongoDb                                                                             |
| :----------------------------------------------------------------------------- | :---------------------------------------------------------------------------------- |
| SQL database are relational databases.                                         | No SQL database are relational databases.                                           |
| They use structured tables to store data in rowa and columns.                  | They provide flexibility in data storage, allowing varied data types and structure. |
| Suitable for applications with well defined schemas and fixed data structures. | Ideal for application with dynamic or evolving data models.                         |
| Examples : MySql,PostgreSQL,Oracle.                                            | Examples: MongoDb,Cassandra,redis                                                   |

### Key features

- Flexible Schema Design

  - MongoDB allows dynamic,schema-less data structures.
  - Easily accommodate changing data requirements.

- Scalability and Performance
  - Horizontal scaling supports large datasets and high traffic.
  - Optimized read and write operations for fast performance.
- DocumentOriented Storage
  - Data is stored in flexible, JSONlike BSON documents.
  - Self-contained units with rich data types and nested arrays.
- Dynamic Queries

  - Rich query language with support for complex queries.
  - Utilize indexes to speed up query execution.

- Aggregation Framework

  - Perform advanced data transformations and analysis.
  - Process data using multiple pipeline stages.

- Open Source and Community
  - MongoDB is open-source with a vibrant community.
  - Regular updates,improvements,and support.

### JSON Vs BSON

- In MongoDB, we write in JSON format only but behind the scene data is stored in BSON (Binary JSON) format, a binary representation of JSON.
- By utilizing BSON, MongoDB can achieve higher read and write speeds,
  reduced storage requirements, and improved data manipulation capabilities,
  making it well-suited for handling large and complex datasets while
  maintaining performance efficiency

`JSON` format : </br>

        {
            "name": "Thapa",
            "age": 29,
            "isStudent": false,
            "scores": [92, 108],
            "address": {
                "city": "Pokhara"
            }
        }

`BSON` format : </br>

    \x1e\x00\x00\x00
    \x02
    name\x00
    \x04\x00\x00\x00Thapa\x00
    \x10
    age\x00
    \x1e\x00\x00\x00\x00\x00\x00\x00
    \x08
    isStudent\x00
    \x00
    \x04
    scores\x00
    \x05\x00\x00\x00\x03\x00\x00\x00
    \x10
    \x00\x00\x00\x00\x00\x00\x00\x00
    \x10
    \x00\x00\x00\x00\x00\x00\x00\x00
    \x10
    \x00\x00\x00\x00\x00\x00\x00\x00
