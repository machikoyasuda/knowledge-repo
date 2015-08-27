## MongoDB

- MongoDB shell is JavaScript based.
- Mongo embeds documents and arrays to reduce need for joints.
- Indexes can include keys from embedded docs & arrays.
- MongoDB is a document database - it stores data as documents, which are similar to JS objects. 

var a = {age: 25}; 
var n = {name: 'Ed', languages: ['c', 'ruby', 'js']}; 
var student = {name: 'Jim', scores: [75, 99, 87.2]};

Database & collections
- A MDB hosts a number of databases, a database holds a set of collections.
- A document is a set of key-value pairs.
- Documents have dynamic schema: documents in the same collection do not need to have a same set of fields or structure, and common fields in a collection's documents may hold different types of data.
- 

=======================

## Commands

- Save:   db.scores.save({a: 99}); 

// "Save the document '{a: 99}' to the 'scores' collection."

- Find doc: db.scores.find(); 

for(i=0; i<10; i++) { db.scores.save({a: i, exam: 5}) }; 

- Find doc where a == 2: db.scores.find({a: 2}); 

- Find doc where a > 15;
db.scores.find({a: {'$gt': 15}});

- $gt - greater than
- $lt - less than
- $lte - less than or equal to
- $ne - not equal
- $gte - greater than or equal to
- $in - is in array
- $nin - not in array

- Update:
- Add db.users
- db.users.save({name: 'Johnny', languages: ['ruby', 'c']}); 
- Update db.users
- db.users.save({name: 'Sue', languages: ['scala', 'lisp']});


- Push & pull items from Arrays: 
- db.users.update({name: 'Sue'}, {'$pull': {'languages': 'scala'} }); 
- db.users.update({name: 'Sue'}, {'$push': {'languages': 'ruby'} }); 

- Delete data
- db.users.remove({name: 'Sue'})
- db.scores.remove();