
## CRUD Commands in MongoDB

As you know, MongoDB is used for various purposes such as application development, data analysis, and more. In all these cases, we need to interact with the MongoDB server to add new data, update existing data, retrieve information, or remove invalid records. 

To facilitate these interactions, MongoDB provides a set of commands that simplify the process. These commands, which make working with MongoDB easier, are known as **CRUD operations**.  

---

### Create Operators:

There are several operators for creating or adding a document to collections in a MongoDB database.  
If the target collection does not exist, MongoDB will create it before adding the new document.  

| Method                        | Description                                             |
|------------------------------|---------------------------------------------------------|
| `db.collection.insertOne()`  | Inserts a single document into a collection.            |
| `db.collection.insertMany()` | Inserts multiple documents into a collection.           |
| `db.createCollection()`      | Creates an empty collection.                            |

As you can see in the image below, a collection named `students` has already been created and contains 4 documents.  
According to the image, we added a new document with the ID of 5 to the collection.  
If the operation is successful, the value of `acknowledged` will be `true`.  

![Insert One](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/insertOne.PNG)    

To simplify the process and to add multiple documents at once, we use the `insertMany()` command.  
As shown in the image below, its input is an array.  
In the image, two new documents related to students with IDs 6 and 7 have been added to the `students` collection.  

![Insert Many](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/insertMany.PNG)  

---

### Read Operators:

The **Read** operator is used to retrieve documents from collections.  
This can be done using the `find()` or `findOne()` methods.  
Often, the `pretty()` method is used immediately after to make the output more readable.  
The `find()` method has several useful operators.

---

### Update Operators:

**Update** operators are designed to apply changes to existing documents in collections.  
To perform such operations, MongoDB provides the following methods:

### Update Methods in MongoDB

| Method | Description |
|--------|-------------|
| `db.collection.updateOne(given criteria)` | Used to update a single document in the collection if it meets the given criteria. |
| `db.collection.updateMany(given criteria)` | Used to update multiple documents in the collection if they meet the given criteria. |
| `db.collection.replaceOne(given criteria)` | Used to replace a document in the collection if it meets the given criteria. |

As shown in the image below, the written command instructs MongoDB to update the first document whose name starts with `std`, changing it to the value `StudentName`. Since the `updateOne` method is used, only the first document that matches the given criteria will be updated.

If the command is executed using the `updateMany` method instead, all documents that meet the specified condition will be updated.

> **Note:** It is recommended to evaluate the conditions using the `find` method before using update commands to avoid unintended data modifications.
### updateOne() Sample:  
![Update One](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/updateOne.PNG)  
### updateMany() Sample:  
![Update Many](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/updateMany.PNG)   

---  

### Delete Operators:

Using the delete operators provided by MongoDB, you can remove documents from collections. To do this, you can use one of the following methods:

| Method                                | Description                                                                 |
|---------------------------------------|-----------------------------------------------------------------------------|
| `db.collection.deleteOne(criteria)`   | Deletes **only one** document that matches the given criteria.             |
| `db.collection.deleteMany(criteria)`  | Deletes **all documents** that match the given criteria.                   |

As shown in the image below, although there are multiple documents that match the condition, only the **first matching document** is deleted when using the `deleteOne()` method.

> The output of the function indicates the number of documents that have been removed from the collection.

### deleteOne() Sample: 

![Delete One](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/DeleteOne.PNG)  
We then execute the `deleteMany()` method with the same condition on the collection. This time, **all documents** that match the condition will be deleted.

As shown in the image below, **4 records** were deleted.  

### deleteMany() Sample:  
![Delete Many](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/DeleteMany.PNG)  







