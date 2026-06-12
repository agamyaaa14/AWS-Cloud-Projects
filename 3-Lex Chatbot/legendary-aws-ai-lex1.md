<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Chatbot with Amazon Lex

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex1)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Build a Chatbot with Amazon Lex

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex1_505be5b8)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate building a chatbot called BankerBot for a fictional banking service using Amazon Lex.

I'm doing this project to learn how chatbots are built using AWS services and to understand the core concepts behind conversational AI, such as intents, utterances, and fallback responses.

### What is Amazon Lex?

Amazon Lex is a service for building conversational interfaces using text and voice.
It uses technologies such as Automatic Speech Recognition (ASR) to convert speech into text and Natural Language Understanding (NLU) to understand what a user is trying to accomplish. This allows developers to create intelligent chatbots without having to build complex AI systems from scratch.


### Key tools and concepts

Services I used were Amazon Lex and AWS IAM.
Key concepts I learnt include:
● Chatbot creation and testing
● Intents
● Utterances
● FallbackIntent
● Initial responses
● Intent confidence scores
● Voice and text interactions

### Personal reflections

One thing I didn't expect in this project was how much planning goes into designing conversations. I initially thought chatbots only needed responses, but I learned that intents, utterances, fallback handling, and response variations all play an important role in creating a good user experience.

### Project timeline

This project took me approximately 1.5 hours.

The most challenging part was understanding how different intents work together, especially the built-in intents such as WelcomeIntent and FallbackIntent.

The most rewarding part was successfully testing the chatbot and seeing it respond correctly to different user inputs through the testing interface.

---

## Setting up a Lex chatbot

### Approach to chatbot setup

In this step, I will create a chatbot from scratch using Amazon Lex because I want hands-on experience with chatbot development and a better understanding of how conversational AI systems are designed.

### Chatbot creation process

I created my chatbot from scratch using Amazon Lex.

Setting it up took me approximately 2 minutes, since Amazon Lex provides a simple interface for creating and configuring chatbots.

### IAM role configuration

While creating my chatbot, I also created a role with basic permissions because Amazon Lex needs permission to interact with other AWS services on my behalf.

I also learned that this role will become important later when integrating Lex with services such as AWS Lambda.

### Intent classification confidence score

I kept the default intent classification confidence score threshold of 0.40.

This means the chatbot must be at least 40% confident that it understands a user's request before matching it to an intent and generating a response.

If the confidence score is too low, the chatbot will trigger the FallbackIntent instead.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex1_97dc2351)

---

## Intents

In this step, I will train BankerBot to greet users because a chatbot should be able to welcome users and guide them toward the services it can provide.

Unlike human customer support, a chatbot can be available at any time to assist users.

### Creating my first intent

Intents represent what a user is trying to achieve during a conversation.

Examples include checking an account balance, transferring money, or requesting support.

I created my first intent, WelcomeIntent, to start conversations with users when they enter greetings such as:
● Hi
● Hello
● I need help
● Can you help me?

When these phrases are detected, BankerBot responds with a welcome message and offers assistance.

I created my first intent, WelcomeIntent, to...inititate conversation with the user when they want to solve a query , by using spmething like hi or hello, or can u help me?, or i need help.. which is when the welcome intent is triggered and greets the user

### Testing chatbot responses

I launched and tested my chatbot successfully.
The chatbot responded correctly when I entered greetings such as:
● Hi
● Hello
● Hiya
● Help me
● Can you help me?

This demonstrated how Amazon Lex can recognize variations of user inputs even if they are not exactly the same as the sample utterances.

---

## Handling unrecognized inputs

My chatbot returned the message "Intent FallbackIntent is fulfilled" when I entered phrases such as:
● How are you?
● Good morning
● What is this?

This happened because these phrases were not closely related to the utterances I had defined for WelcomeIntent, so Lex could not confidently determine the correct intent.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex1_505be5b8)

---

## Configuring FallbackIntent

In this step, I will customize FallbackIntent because users should receive a helpful response when the chatbot does not understand their request.

A technical message such as "Intent FallbackIntent is fulfilled" would not be meaningful to most users.

### When FallbackIntent triggers

FallbackIntent is a default intent in Amazon Lex that is triggered whenever the user's input does not match any configured intent with sufficient confidence.

It acts as a safety mechanism for handling unknown or unsupported requests.

I wanted to configure FallbackIntent so that BankerBot could guide users toward supported banking-related requests instead of simply displaying an error message.
This creates a much better user experience.

### My FallbackIntent configuration

To configure FallbackIntent, I customized the closing response with a friendly message that explained what BankerBot could help with and encouraged the user to rephrase their request.

The response suggested banking-related actions such as:
● Checking account balances
● Transferring funds
● Making payments

I also added response variations so the chatbot would not always return the same message.

Adding variations means Amazon Lex can randomly choose from multiple responses whenever FallbackIntent is triggered.

For users, this creates a more natural and conversational experience because the chatbot does not sound repetitive.

---

## FallbackIntent with Variations

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex1_c4fc89af)

---

## Initial Responses

In this project extension, I'm about to enhance BankerBot by adding initial responses and response variations to the FallbackIntent.

I'm doing this so that the chatbot feels more conversational and engaging before providing its final fallback response.

### Setting up initial responses

Initial responses are messages sent immediately after Amazon Lex recognizes an intent and before the rest of the conversation flow continues.

They help acknowledge the user's request and improve the overall user experience.

I've configured initial responses for my FallbackIntent using messages such as:
● "Hmmm, this is interesting..."
● "One moment..."
● "Yikes, let me think about that..."

### Initial response implementation

The initial response messages I set up are designed to make BankerBot sound more friendly and conversational.

I also created multiple variations so users receive different acknowledgements instead of seeing the same message repeatedly.

For the user, this means interactions feel more natural and engaging, even when the chatbot does not fully understand the request.

This extension showed me how small design choices can significantly improve the quality of a chatbot experience.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex1_09bcb9701)

---

---
