# MongoDB Database
## Create a noSQL Database in MongoDB.

In MongoDB there is no create database style command, or anything like that, what mongodb does is **create a collection (database)** at the moment an object or document is inserted *(we can say we are recording a table)* in that collection.

To create a Databese in MongoDb you need to use (withe the sentence *use*), a database or a collection that doesn't exist yet.

`use movies;`

Now we are going to insert a movie in the collection and at that moment it will be created:

`db.movies.save({title:'Spiderman'});`

Now we have created a record and the database at the same time, although in mongo we really create collections and save **json documents.**

We can do a query to see what is inside the collection:

`db.movies.find();`

And we will receive this:

```
> use movies
switched to db movies
> db.movies.save({title:'Spiderman'});
WriteResult({ "nInserted" : 1 })
> db.movies.find();
{ "_id" : ObjectId("581c73028457b4u049bec72c98"), "title" : "Spiderman" }
```
### EXTRA
We can see all the datbases creates with the command:
`show dbs;`

> Clarification: We have a database called movies and within it we have a collection of documents that is also called movies, in which we save data and query data with find, we could have as many collections of objects as we want.

***Let's talk now about how to create a connection to MongoDB from NodeJS***

## Connection to MongoDB from NodeJS. RESTful API with Node

First of all we should have installed MongoDB.

After creating a DB we are going to connect NodeJS with MongoDB. In the folder's project that we have created we need to create the file `index.js`

And we will add this:
```
// Use new features of Ecmascript 6
'use strict'

// We load the mongoose module to be able to connect to MongoDB
var mongoose = require('mongoose');

// We tell Mongoose that we will make the connection with Promises
mongoose.Promise = global.Promise;

// We use the connect method to connect to our database
mongoose.connect('mongodb://localhost:27017/my_mongo_database', {useMongoClient: true})
    .then(() => {
        // When the connection is made, we launch this message by console
        console.log('The connection to MongoDB was successful !!');
    })
    .catch(err => console.log(err));
    // If it doesn't connect correctly we spit out the error
```

With this we have already made the connection to MongoDB from NodeJS in a simple way using Mongoose.

### MongoDB Problems

If you have problems with Mongoose you can check my [repository](https://github.com/yumewebs/MongoDB-Problems/blob/main/README.md) where I'm fixing few problems with **MongoDB and Mongoose**
