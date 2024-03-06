Databse are modular systems and consist of multiple parts: 

1. A transport layer accepting requests
2. A query processor determining the most efficient way to run queries
3. An execution engine carrying out the operations
4. A storage engine

The storage engine (or database engine) is a software component of a database management system responsible for storing, retrieving, and managing data in memory and on disk, designed to capture a persistent, long-term memory of each node [REED78]. While databases can respond to complex queries, storage engines look at the data more granularly and offer a simple data manipulation API, allowing users to create, update, delete, and retrieve records. One way to look at this is that database management systems are applications built on top of storage engines, offering a schema, a query language, indexing, transactions, and many other useful features.

