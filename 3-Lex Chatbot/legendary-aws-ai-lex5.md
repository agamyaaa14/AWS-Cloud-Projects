<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Multiple Slots in a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex5)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Build a Chatbot with Multiple Slots

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex5_67890123)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is an AWS service for building conversational interfaces using voice and text, powered by Natural Language Understanding (NLU). It is useful because it handles language processing automatically, letting us build natural human-like flows without deep AI expertise. 

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to handle complex transactional intent (transferring money) by reusing a single slot type (accountType) for distinct functional roles (source vs. target) and confirming details before fulfillment.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how I could use CloudFormation to do all the work I had done in 5 days to do it in just 5 minutes, realllyyy cool stuff.

### This project took me...

This project took me almost 3 hours.

---

## TransferFunds

An intent I created for my chatbot was TransferFunds, which contains 3 slots– for souce account, target account, and transfer amount. In addition to that I also set up confirmation prompts.


![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex5_67890123)

---

## Using multiple slots

For this intent, I had to use the same slot type (accountType) twice. This is because both the origin and destination require the exact same set of acceptable values. However, assigning them unique slot names (sourceAccountType and targetAccountType) acts as defining distinct variables. This tells our chatbot's fulfillment logic exactly which account to debit and which to credit, preventing any routing confusion during the transfer process.

I also learnt how to create confirmation prompts, which are the prompts given to the user by the bot to confirm a specific action to execute.
If the user confirms the action the intent is executed otherwise it defaults to the decline response which is set up by me.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex5_97dc2351)

---

## Exploring Lex features

Lex also has a special conversation flow feature that shows every step of the conversation with the bot in a logical, chronological order. It also shows recommendations for what we could add to the intent  set up, just clicking on them enables us to edit them to make necessary changes.
The flow is updated syncronously with any changes that is made.

You could also set up your intent using a visual builder! A visual builder is as the name suggests a visual representation of the intents I have built, it is possible to build all the intents from scratch using this feature.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex5_12345678)

---

## AWS CloudFormation

AWS CloudFormation is service that gives you an easy way to create and set up AWS resources.

It's an infrastructure as code service - meaning you will use a file that describes all the resources you want to create and their dependencies as code. Then, you can use that template to create, update, and delete the entire stack of resources you described, instead of managing your resources individually

I used CloudFormation to speed up the process of building BankerBot.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex5_c4fc89af)

---

## The final result!

Re-building my bot with CloudFormation took me 5 minutes.

There was an error after I deployed my bot! The error was Access Denied while invoking Lambda function.
I fixed this by editing the policy statement under the Permissions tab in Lambda function by specifying the "Souce ARN" that was shown when I was testing the bot.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex5_505be5b8)

---

## Using the visual builder

Using the visual builder, I added a conditional transition node to route active user contexts dynamically. What this means for an end user is a seamless conversational experience where they can switch tasks mid-flow—like jumping to check their balance during a money transfer—without encountering dead-ends or having to manually restart the session.

The new Get slot value card will trigger when after the transfer is complete.
This card will try to capture if the user also wants to check account balance after transfer.
If the answer is "Yes" then the conversation directs to the conditional card otherwise it directs the flow to the Fallback intent.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex5_9cac15cd4)

---

---
