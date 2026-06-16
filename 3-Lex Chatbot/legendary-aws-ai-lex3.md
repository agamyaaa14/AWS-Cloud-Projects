<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect Amazon Lex with Lambda

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex3)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Connect Amazon Lex with Lambda

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex3_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is an AWS service used to build smart chatbots and voice assistants that can interact naturally with users through text or voice.

It is useful because it can connect a chatbot's conversational flow to backend services such as AWS Lambda, allowing the chatbot to process requests, retrieve information, and perform actions beyond simple responses.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to connect my CheckBalance intent with an AWS Lambda function so that BankerBot could return a bank balance instead of just collecting user information.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how useful aliases are. I learned that aliases can point to different versions of a chatbot and can be updated without changing the applications connected to them. This makes testing and deploying new versions much easier and saves developers a lot of time.

### This project took me...

This project took me approximately 1 hour and 30 minutes.

---

## AWS Lambda Functions

AWS Lambda is a service that runs your code only when triggered by an event, without requiring you to manage any servers. It automatically shrinks or grows to handle any amount of traffic instantly. You only pay for the exact milliseconds your code spends processing requests.

In this project, I created a Lambda function to generate random account balances whenever a user asks BankerBot to check their balance.

Since we do not have access to a real banking database, the Lambda function simulates account balances by generating random values. This helped me understand how a chatbot can retrieve information from backend services and return it to users.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex3_97dc2351)

---

## Chatbot Alias

An alias is a permanent nickname or shortcut that points to a specific version of your chatbot. Instead of updating your entire app every time you release a new bot version, you just change where the nickname points. This keeps your app connected smoothly without changing a single line of external code.

TestBotAlias is the default testing version of my chatbot.
It provides a safe environment where I can test new features, integrations, and updates before using them in a production environment.

To connect Lambda with my BankerBot, I opened my bot's TestBotAlias and selected the English (US) language configuration.

From there, I associated the Lambda function called BankingBotEnglish and selected $LATEST as the function version so that the chatbot would always use the most recent version of my Lambda code.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex3_c4fc89af)

---

## Code Hooks

A code hook is a mechanism that allows Amazon Lex to invoke an AWS Lambda function during a conversation.

Code hooks are useful when a chatbot needs to perform actions that require custom logic, such as querying a database, processing information, validating user input, or generating dynamic responses.

Even though I already connected my Lambda function with my chatbot's alias, I had to use code hooks because the chatbot still needed a direct connection between the CheckBalance intent and the Lambda function.

Connecting Lambda to the alias only makes the function available to the bot. The code hook tells Lex exactly when it should call that function during the conversation.

I could find code hooks at the CheckBalance intent under the Fulfilment section.

I expanded the "On successful fulfilment" settings, opened the advanced options, and enabled the Lambda fulfilment code hook so the intent could trigger my Lambda function after collecting all required information from the user.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex3_505be5b9)

---

## The final result!

I've set up my chatbot to trigger Lambda and return a random dollar figure when the user provides a valid account type and date of birth during the CheckBalance conversation.

Once the required slot values are collected and validated, the chatbot invokes the Lambda function, which generates a random account balance and returns it to the user.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex3_505be5b8)

---

## Customizing the Lambda function

To level up the connection between Lambda and Lex, I modified the Python code inside my Lambda function to generate more personalized responses instead of returning a plain balance message.

I added a list of creative descriptions and used Python's random.choice() function to select one each time the chatbot responds.

This made the chatbot's replies feel more dynamic and engaging.

Now, the message my users see when they ask for their bank balance is a customized response that includes my name along with a randomly selected description and the generated account balance.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex3_38b5f5691)

---

---
