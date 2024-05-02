# Inserting data in MongoDB 

## We can insert data from the shell

```shell

# enter db command to get the current database
db
test
Atlas atlas-10vfl0-shard-0 [primary] test

# to switch databases 
use sample_sjo_music
switched to db sample_sjo_music

# to insert one document
db.albums.insertOne(db.albums.insertOne({title:"The Steps Mix", duration:1500, date:new Date()})) 

# confirmation that the document has been inserted correctly

{
  acknowledged: true,
  insertedId: ObjectId('6633afa2a35758d767288137')
}
```

## Insert without using the Date() function

```shell

# example 1
db.albums.insertOne(db.albums.insertOne({title:"The Steps Mix", duration:1500, date: Date("2023-05-06T00:00:00.000Z")})) 
{
  acknowledged: true,
  insertedId: ObjectId('6633b2e2a35758d767288139')
}

```
## Insert document with complex structure

```shell
db.albums.insertOne({title:"The Steps Mix",duration:1500,date:new Date("2020-05-06T00:00:00Z"),formats:{vinillo:true,cd:true,cassette:true}})
{
  acknowledged: true,
  insertedId: ObjectId('6633b469a35758d76728813a')
}
```

## Insert document with complex structure - ARRAY

```shell
db.albums.insertOne({title:"The Steps Mix", duration:1500,group:"HAIM",date:new Date("2020-05-06T00:00:00Z"), formats:{vinillo:true,cd:true,cassette:true}, song:[{code: new ObjectId(),name:"The Steps", duration:120}, {code:new ObjectId(),name:"Summer Girl", duration:150}, {code: new ObjectId(), name:"Nom I'm in it",duration:120}]})

{
  acknowledged: true,
  insertedId: ObjectId('6633bfd2a35758d76728813e')
}
```

## Insert many documents at once

```shell
# using the insertMany() function we can insert multplie docs in array format

db.albums.insertMany([{title:"Made in Japan", group:"Deep Purple"}, {title:"Made in Europe", group:"Deep Purple"}])

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6633c265a35758d76728813f'),
    '1': ObjectId('6633c265a35758d767288140')
  }
}

```

# Update 

## Update document using key field (id)

```shell
# we use a updateOne() because using the id we will identify a unique document.

db.albums.updateOne({_id:ObjectId("6633bfd2a35758d76728813e")}, {$set:{duration:1700}})

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

```

## Update multiple documents at the same time

```shell
# the first parameter is the like WHERE from sql, it's the condition

db.albums.updateMany({duration:1500},{$set:{duration:1600}})

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 4,
  modifiedCount: 4,
  upsertedCount: 0
}

```

## Update complex field document 

```shell
db.albums.updateOne({_id:ObjectId("6633bfd2a35758d76728813e")}, {$set:{"formats.cassette":false}})

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

```

# Delete

## Delete a single document 

```shell
db.albums.deleteOne({_id:ObjectId("6633bfd2a35758d76728813e")})

{
  acknowledged: true,
  deletedCount: 1
}
```

# Finding data 

## The find() function is very similar to SELECT from SQL

```shell

# this query will pull up all the documents in the db

db.albums.find()

```

