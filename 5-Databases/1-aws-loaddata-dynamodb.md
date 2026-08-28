<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Load Data into DynamoDB

**Project Link:** [View Project](http://nextwork.ai/projects/aws-databases-dynamodb)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Load Data into a DynamoDB Table

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-dynamodb_b481c730)

---

## Introducing Today's Project!

### What is Amazon DynamoDB?

Amazon DynamoDB is a fast, flexible NoSQL database service. It is highly useful because it uses partition keys for lightning-fast lookups and doesn't lock you into a rigid, table-wide schema.

### How I used Amazon DynamoDB in this project

In today's project, I used Amazon DynamoDB to build tables like NextWorkStudents, ContentCatalog and others with specific attributes, and then loaded sample data records using the CLI. I also edited individual items to practice adding custom attributes.


### One thing I didn't expect in this project was...

One thing I didn't expect in this project is for the CLI to create tables in seconds when the console took minutes! It was also amazing to see different items hold totally different fields and still make complete sense in NoSQL.

### This project took me...

The actual project setup took about 30 minutes, but I spent 1.5 hours overall because I was actively learning and documenting everything as I went!

---

## Create a DynamoDB table

DynamoDB tables organises data using items and their respective attributes, along with partition keys for easy and fast querying.

It can be understood better with the help of this analogy:
● Think of a DynamoDB table as a digital filing cabinet where each folder is an item holding a flexible stack of papers called attributes.
● Every folder has a unique tab label, the partition key, which lets you grab that exact folder instantly without browsing the rest of the cabinet.

An attribute is like a piece of data about an item. In this case, the item is Nikko and the attribute is the number of projects Nikko completed.

Each item in DynamoDB can have multiple attributes. But, unlike relational databases where each row in a table must have the same columns, DynamoDB items can have their own unique set of attributes.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-dynamodb_a3cefee0)

---

## Read and Write Capacity

Read capacity units (RCUs) just means how many read operations a DynamoDB engine can perform in one second.
Here a DynamoDB engine can perform 2 read operations ina single second.

Write capacity units (WCUs) are just like RCUs but they give the DynamoDB tables the engines to edit/update/delete data.
1 WCU = 1 item write/second

So ulimately that means it costs more to run write operations than read operations.

Amazon DynamoDB's Free Tier covers 25GB of data storage, plus 25 Write and 25 Read Capacity Units (WCU, RCU), which is enough to handle 200M requests per month all for free.

Auto scaling can automatically adjust database's performance based on real-time demand.
But I turned off auto scaling because if it's not monitored, it has the power to boost the table's processing power (for eg: in case the table needs to perform lots of write/write updates), auto scaling can push the table's settings to go over Free Tier limits!

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-dynamodb_ef47dd8f)

---

## Using CLI and CloudShell

AWS CloudShell is the shell in AWS Management Console, which means it's a space to run code! The awesome thing about AWS CloudShell is that it already has AWS CLI pre-installed.

AWS CLI is a software that lets us to create, delete and update AWS resources with commands instead of navigating and clicking to find stuff through the AWS console.

I ran a CLI command in AWS CloudShell that created 4 more tables along with NextWorkStudents called–
Comment, ContentCatalog, Form and Post.

Each table has specfic attributes and settings–
● ContentCatalog Table: This table has a numeric attribute called Id.
● Forum Table: This table has a partition key called Name.
● Post Table: This table has a partition key called ForumName and a sort key called Subject. We'll dive into sort keys soon!
● Comment Table: This table has a partition key called Id and a sort key called CommentDateTime.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-dynamodb_81e0258b)

---

## Loading Data with CLI

I ran a CLI command in AWS CloudShell that loads the data of all four files into DynamoDB using AWS CLI's batch-write-item command.

● aws dynamodb batch-write-item command is used to load or insert multiple items into DynamoDB tables

● --request-items tells DynamoDB that the items are currently stored inside a file that it'll need to retrieve from.

● file:// then tells DynamoDB that the file is stored locally in the CloudShell environment, with the name FILENAME.json.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-dynamodb_791c600b)

---

## Observing Item Attributes

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-dynamodb_b481c731)

I checked a ContentCatalog item, which had the following attributes:
Author, ContentType, Difficulty, Price, ProjectCategory, Published, Title and URL.

I checked another ContentCatalog item, which had a different set of attributes like:
ContentType, Services, Price, Title, URL, and VideoType.


---

## Benefits of DynamoDB

A benefit of DynamoDB over relational databases is flexibility, because every item can have its own unique attributes instead of being locked into a rigid schema. This means we can add a custom field to one item without forcing every other record in the table to have it too!

Another benefit over relational databases is speed, because it uses partition keys to find and grab the exact data we want instantly. Unlike relational databases that have to search through the entire table row-by-row, DynamoDB stays lightning-fast!

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-databases-dynamodb_b481c730)

---

---
