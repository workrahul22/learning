### Check mongo version

```javascript
    db.version()
```

### MongoDB CRUD Operations
```javascript
    db.collection.insertOne()
    db.collection.insertMany()
    db.collection.find({
        age: {$gt: 18}, 
        status: {$in: ["A", "D"]}
    }, 
    {name: 1, address: 1})
        .limit(5)
    db.collection.find({$or: [{status: "A"}, {qty: {$lt: 30}}, {item: {$regex: '^p'}}]})
    db.collection.updateOne()
    db.collection.updateMany()
    db.collection.replaceOne()
    db.collection.deleteOne()
    db.collection.deleteMany()
```

### In MongoDB, insert operations target a single collection. All write operations in MongoDB are atomic on the level of a single document.

### If the collection does not currently exist, insert operations will create the collection.

### In MongoDB, each document stored in a collection requires a unique _id field that acts as a primary key. If an inserted document omits the _id field, the MongoDB driver automatically generates and ObjectId for the _id field.

### This also applies to documents inserted through update operations with upsert: true

### All write operations in MongoDB are atomic on the level of a single document.

### Write Acknowledgement: With write concerns, you can specify the level of acknowledgement requested from MongoDB for write operations.
