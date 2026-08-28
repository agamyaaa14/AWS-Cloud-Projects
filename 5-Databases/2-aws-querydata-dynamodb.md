<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Query Data with DynamoDB

**Project Link:** [View Project](http://nextwork.ai/projects/aws-databases-query)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Query Data with DynamoDB

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-query_733d9399)

---

## Introducing Today's Project!

### What is Amazon DynamoDB?

Amazon DynamoDB is a fast, fully managed NoSQL database. It is useful because it offers single-digit millisecond latency at scale and has a flexible, schemaless structure that allows items to have unique attributes.

### How I used Amazon DynamoDB in this project

I created tables, loaded data using CLI, scanned/queried items using keys, and filtered attributes. I also used a CLI transaction to update multiple tables simultaneously, ensuring overall data consistency.

### One thing I didn't expect in this project was...

I didn't expect that queries strictly require a partition key. It can be a drawback if you don't know the key but have other details, which shows why upfront data modeling is absolutely vital in NoSQL.

### This project took me...

This project took me about 2 hours of focused learning to complete, from setting up tables in the console to running advanced queries and transactions in the CLI!

---

## Querying DynamoDB Tables

A partition keys are like tags that DynamoDB uses to organise the table's data. When searching for an item in a table, DynamoDB will need its partition key to ensure faster search and results!
Partition key values don't have to be unique. For example if "Color" is a partition key, items can share partition key values like "Blue", "Green", "Red" and more.

A sort key is a secondary key used to filter the query results again! Sort keys work after the partition key i.e. we still have to use the partition key to split up the data first, and then the sort key partitions the data again.

Sort keys are optional, which is why the previous query for ContentCatalog table could still work without one!

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-query_d105b0b0)

---

## Limits of Using DynamoDB

I ran into an error when I queried for comments by User Abdulrahman. This was because I cleared the partition key. DynamoDB requires a specific partition key to run a Query, unlike relational SQL databases where you can query any column freely.

Insights we could extract from our Comment table include all comments left on a specific post over a certain time range (using partition and sort keys). 

Insights we can't easily extract include comments made by a specific user across all different posts, because User is not part of our partition key.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-query_cb3e260c)

---

## Running Queries with CLI

A query I ran in CloudShell was get-item on ContentCatalog with ID 202. This query will retrieve specific attributes (Title, ContentType, Services) using an eventually consistent read and return the exact capacity units consumed.

Query options I could add are --consistent-read for the most updated data, --projection-expression to select specific attributes (reducing data size), and --return-consumed-capacity to measure performance and cost by showing RCU consumption.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-query_733d9399)

---

## Transactions

A transaction is a group of operations that all have to succeed - if any of the operations in the group fails, none of the changes get applied. This makes sure that any change to your database is consistent across all the tables.


I ran a transaction using AWS CloudShell CLI. 
This transaction did two things-
●  Adding a new item to the Comment table with all the details of the user is named Connor.
● Updating the Forum Table - Connor's comment was made on a post in the Events forum, so the number of comments in that forum should go up by 1.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-query_2f65f83e)

---

---
