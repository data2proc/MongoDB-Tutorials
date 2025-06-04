# What is Aggregation in MongoDB?

Aggregation operators process documents/rows and return a computed value as output. The process works by first collecting various documents, then categorizing them into groups, and finally applying specific operators like `sum`, `average`, `minimum`, `maximum`, etc., on those groups. MongoDB performs this operation in three ways:

## • Aggregation Pipeline

This is the recommended method for performing aggregation tasks in MongoDB. It is designed with performance optimization in mind. In this method, the designed pipeline can either produce no output, generate new documents, or filter existing ones.

Essentially, an aggregation pipeline is a sequence of aggregation operators that process, transform, and return output. The output of each stage is passed as the input to the next stage for further processing.

Input -> $match -> $group -> $sort -> Output  

In the example above, the input refers to one or more documents. The output of each stage is passed to the next stage. These three intermediate stages are collectively referred to as the **Aggregation Pipeline**. Using this pipeline helps us break queries into smaller, simpler steps. The order of these stages has been reviewed, and it is recommended to follow this sequence to achieve better performance.

To make this concept clearer, let’s walk through an example:  

![Alt Text](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Pipeline01.PNG)  

First, we add 4 documents with the information shown in the image above to the collection.  
Then, we use the command shown in the image below to calculate the total tuition fees for department A.  
As you can see, the total tuition for all students in department A will be 32.    

![Alt Text](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Pipeline02_sum.PNG)    

## How Aggregation Works in MongoDB

As you can see, in the first part — the `$match` stage — you can filter data. This step significantly improves query performance because it excludes documents that do not meet the condition. You can also use other aggregation functions besides `$sum`.

Next, we will explain the available operators that can be used in the aggregation pipeline:

MongoDB offers a wide range of operators for use in each stage of aggregation. Each of these operators prepares the input for the next stage in the pipeline.

Arguments can be passed to operators in two specific formats:

```js
{ <operator>: [<argument1>, <argument2>, ...] }
{ <operator>: <argument> }
```
For more detailed information on these operators, visit:
[MongoDB Aggregation Operators](https://www.mongodb.com/docs/manual/reference/operator/aggregation/)

### In Summary, Here Are the Operator Categories Used in the Aggregation Pipeline:
+ Mathematical operators  

+ Array-specific operators  

+ Logical expression operators  

+ Comparison operators  

+ Conditional operators  

+ Customized aggregation operators  

+ Data size operators  

+ Date-related operators  

+ Object-based operators  

+ Set-specific operators  

+ Text string operators  

+ Text search operators  

+ Trigonometric expression operators  

+ Data type operators  

+ Aggregation operators  

+ Variable operators  

## What Are Aggregation Stages in MongoDB's Pipeline?  
Each stage can transform the data and prepare it for the next stage. A stage can produce multiple outputs, which are then passed as inputs to the next stage. This continues until the final result is displayed as output.

MongoDB provides two ways to perform aggregation:

db.collection.aggregate() — used in the shell

db.aggregate() — another method you can use

Each stage can be repeated in the pipeline except for $out, $merge, and $geoNear, which can only be used once.

## The 7 Most Common Aggregation Stages:  
- $project  
Transforms documents by adding or removing fields to prepare them for the next stage.

- $match  
Filters documents according to specific conditions. This and the $project stage are the most performance-impacting stages.

- $group  
Groups documents using a unique identifier and applies aggregation functions to each group.

- $sort  
Sorts the documents received from the previous stage and passes them unchanged to the next.

- $skip  
Skips the first n documents as needed and forwards the rest unchanged.

- $limit  
Limits the number of documents passed to the next stage.

- $unwind  
Since you can't directly access array elements from the $group stage, $unwind breaks down arrays and outputs each element as a separate document.  

## Other Aggregation Methods in MongoDB

### • Map-Reduce Function

In this method, JavaScript functions are used to perform the mapping and reducing operations for aggregation.  
You are required to implement these functions manually and then use them in your operations.  
Because of this, it is not efficient in terms of performance and speed.

### • Single-purpose Aggregation

This method provides simple access to common aggregation operations, such as counting the number of documents in a collection or returning unique documents.  
However, its biggest drawback is the lack of flexibility and fewer capabilities compared to the other two methods.
