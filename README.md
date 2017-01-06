  # Prime Mongo Shell Peer Challenge

Now that you've learned some of the basics of querying MongoDB via the mongo shell, use that information to query a collection of bios. Remember to switch off with your partner half-way through this exercise.

Check out these docs for more advanced find queries https://docs.mongodb.org/getting-started/shell/query/#specify-conditions-with-operators

## Instructions

### Setup

1. Load the data using this command `mongoimport --db challenge --collection bios --drop --file bios.json`
2. Start the Mongo shell with `mongo`.
3. Connect to the `challenge` database using the mongo shell command `use challenge`

### Queries

Create a file, `queries.js` that will contain the queries that correctly address the criteria in the
steps that follow.

1. Find documents that have awards.
db.bios.find({"awards" : {$exists:true}})

2. Find documents that don't have awards.
db.bios.find({"awards" : {$exists:false}})

3. Find documents that have contribs for OOP or UNIX.
db.bios.find({ $or: [{"contribs": "unix"}, {"contribs": "OOP"} ]} )

4. Find documents with "Turing Award" awards.
db.bios.find( {"awards.award" : "Turing Award"}).pretty()

5. Find documents with IDs between 3 and 7.
db.bios.find( {"_id"  :   {$gt : 3  ,  $lt : 7 } } )

6. Find documents with awards that were awarded before the year 2000.
db.bios.find( {"awards.year" : {$lt:2000}} )

7. Find documents with birth dates, but no death dates.
db.bios.find({$and : [{"birth" : {$exists:true}}, {"death" : {$exists:false}}] }).pretty()
