<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# AI Finance Agent with Amazon Bedrock

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-genai-bedrock-agent)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

---

## Introducing Today's Project!

In this project, I will build an AI finance agent using Amazon Bedrock.

I'm doing this project to learn how AI agents can be built for specific real-world use cases like finance, and how AWS Bedrock can automate tasks such as analyzing spending data and giving budget suggestions.

### Key services and concepts

The key tools I used include Amazon Bedrock, Amazon Nova Lite, and Code Interpreter.
Key concepts I learnt include prompt engineering, session management, agent memory, AI reasoning, and how agents can execute Python code automatically to analyze data.

### Challenges and wins

This project took me approximately 1 hour.

The most challenging part was managing sessions and updating instructions correctly, because sometimes the updated prompt changes would not reflect immediately in the next session.

The most rewarding part was seeing the agent remember context from previous sessions and give responses based on earlier conversations.

---

## Exploring Amazon Bedrock and Foundation Models

In this step, I am navigating to my AWS account and Amazon Bedrock to explore the Amazon Nova Lite model and preview Bedrock Agents, because I will use these tools to build my AI finance advisor.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_w5x8n1q4)

### Understanding foundation models

A foundation model is a large pre-trained AI model that can perform many tasks through prompts instead of separate training.

We are using Amazon Nova Lite because it is fast, lightweight, cost-effective, and already available inside AWS without additional setup.

### Discovering Bedrock Agents

A Bedrock Agent is an AI system that can perform tasks autonomously instead of only answering questions like a normal chatbot.

Unlike a chatbot, an agent can reason through tasks, execute code, analyze files, and decide what actions to take based on instructions.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_h4t7y1a5)

---

## Creating the AI Finance Agent

In this step, I will:
● Create an Amazon Bedrock Agent as a personal finance advisor
● Write instructions that define how the agent should behave
● Enable Code Interpreter so the agent can write and execute Python code automatically

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_q4j6r2m8)

### Crafting the agent instructions

I wrote instructions to guide the AI agent to analyze spending patterns, categorize expenses, and suggest budget improvements clearly.

This is important because the instructions act like the agent’s personality and operating rules, and better instructions usually lead to better outputs.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_f2d8g4l6)

---

## Analyzing Spending Data with Code Interpreter

In this step, I will:
● Upload a transactions CSV file and get a spending summary from the agent
● Request budget recommendations
● Improve the agent’s output by refining the instructions

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_p4r7t9v1)

### How Code Interpreter processed the data

I uploaded a CSV file containing financial transactions along with a prompt asking the agent to analyze spending by category.

The agent used Code Interpreter to automatically generate and execute Python code, which processed the CSV file and calculated the spending totals.

The output displayed different spending categories along with their corresponding costs and breakdowns.

---

## Iterating on Agent Instructions with Traces

I updated the instructions to display dollar amounts with two decimal places and include percentage breakdowns for each category.

The output improved because the agent followed the refined instructions more accurately and even organized the results into a cleaner table format.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_q5s8u2w4)

---

## Enabling Cross-Session Agent Memory

In this project extension, I am enabling:
● Agent memory with session summarization
● Spending preference tracking across sessions
● Context recall from previous conversations

Cross-session memory is important because normally an AI conversation resets after every session. By enabling memory, the agent can remember previous discussions and continue conversations more naturally later.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_n5m3k7j1)

### Session summarization vs full history

I configured session summarization, which is the memory type supported by Bedrock Agents.

After each session ends, the agent stores a summary of important discussions instead of the full conversation history.

This is useful because it is more efficient and avoids storing unnecessarily long conversations.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-agent_t8h1g5f3)

### Testing cross-session recall

In this project extension, I tested cross-session memory recall.
The agent successfully remembered information and spending preferences from a previous session, which showed that the memory feature was working correctly.

---

## Wrapping Up

I did this project to learn how AI agents can be created using Amazon Bedrock to autonomously analyze data and perform tasks using prompts instead of manually writing all the logic myself.
I also learned how Code Interpreter, prompt engineering, traces, and memory systems work together to make AI agents more intelligent and useful.

Another skill I want to learn next is building multi-agent AI systems for more advanced real-world use cases.

---

---
