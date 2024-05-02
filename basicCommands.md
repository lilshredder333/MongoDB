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

# Insert without using the Date() function

```shell

# example 1
db.albums.insertOne(db.albums.insertOne({title:"The Steps Mix", duration:1500, date: Date("2023-05-06T00:00:00.000Z")})) 

# example 2
db.albums.insertOne({title:"The Steps Mix",duration:1500,date:new Date("2020-05-06T00:00:00Z"),formats:{vinillo:true,cd:true,cassette:false}})
```

# Finding data 

## The find() function is very similar to SELECT from SQL

```shell

# this query will pull up all the documents in the db

db.albums.find()

```

