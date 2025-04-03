# mongodb-playground

### Log Into Mongo DB Via Mongosh Shell

`$ mongosh "mongodb://localhost:27017" --username mt --password pw`

OR

`$ mongosh "mongodb://mt@pw:localhost:27017/coolDb"`

** Need to make sure that mt is authorized on coolDb database first! by executing `$ db.getUser("mt")`on the specific database.

Docs: https://www.mongodb.com/docs/mongodb-shell/

### Common commands to use on mongosh:

```
$ show dbs

$ use <database_name>

$ show collections

$ db.<collection>.find()

$ db.<collection>.countDocuments()

$ use newDatabase
NOTE: `$ use newDatabase` will create a new database. If it does not exist, a new one will be created!
Then to make sure db is created, insert at least one document into a collection within the db. MongoDB is schema-less and can store any data structures or format.

$ db.newCollection.insertOne({ name: "Bob", age: 37})

$ db.newCollection.insertMany([
  { name: "Alice", age: 30 },
  { name: "Bob", hobbies: ["reading", "hiking"] },
  { name: "Charlie", address: { city: "New York", zip: "10001" } }
])

$ db.newCollection.find()
NOTE: To show all document within a collection.

$ db.newCollection.find({ name: "Bob"}).pretty()
NOTE: To find a document with specific field and value. Can find using regex too or with multiple fields.

$ db.grantRolesToUser("mt", [{ role: "readWrite", db: "customerdb" }])
NOTE: Need to grant permission to new database! Or create new user! There is a default credential but it will not apply to new databases created. Hence, you might run into authorization issues in your app or on command line!

$ db.createUser({ user: "mt", pwd: "pw", roles: [{ role: "readWrite", db: "customerdb" }] })
```
