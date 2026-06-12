<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Add Custom Slots to a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex2)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Add Custom Slots to a Lex Chatbot

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex2_c4fc89af)

---

## Introducing Today's Project!

In today's project, I used Amazon Lex to build custom slots that allow BankerBot to collect important information from users, such as their account type and date of birth, so it can help them check their account balance more efficiently.

### What is Amazon Lex?

Amazon Lex is an AWS service for building conversational chatbots using text and voice.

It is useful because it provides built-in natural language understanding and allows developers to create chatbots that can collect information, understand user requests, and guide conversations without building complex AI systems from scratch.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how intelligently Lex handled repeated invalid inputs. After the user failed to provide a valid date of birth several times, Lex automatically assumed there might be a larger misunderstanding and attempted to switch to a different intent. It was interesting to see how much thought goes into handling real user behavior.

### This project took me...

This project took me approximately 1 hour.

---

## Slots

Slots are pieces of information that a chatbot needs to collect before it can complete a user's request.

They act like fields in a form, allowing the chatbot to gather important details from users during a conversation.

By adding custom slots in utterances, my chatbot's users can provide information naturally as part of their message instead of answering multiple follow-up questions.

If Lex detects a valid slot value in the user's message, it automatically fills the slot, making the conversation faster and smoother.

In this project, I created a custom slot type to build custom slots that allow BankerBot to collect important information from users, such as their account type and date of birth, so it can help them check their account balance more efficiently.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex2_97dc2351)

---

## Connecting slots with intents

This slot type has restricted slot values, which means only the account types that I explicitly defined will be accepted as valid values.

This prevents the chatbot from accepting unsupported account types and helps keep conversations accurate and relevant to the banking services offered.

I associated my custom slot with CheckBalance, which is an intent that helps users check their account balance.

The chatbot collects both the account type and date of birth to verify the user's information before proceeding with the balance request.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex2_c4fc89af)

---

## Slot values in utterances

I included slot values in some of the utterances (i.e. user inputs) by adding placeholders such as:
"What is the balance in my {accountType} account?"

For example, if a user says:
"What is the balance in my savings account?"

Amazon Lex automatically recognizes "savings" as the accountType slot value and fills it without needing to ask the user again.
This creates a more natural and efficient conversation.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex2_505be5b8)

---

## Handling failures in slot values

I added variations for the dateOfBirth slot prompt, such as... 
Message 2:
"Sorry, that wasn't clear to me. What's your date of birth?"

Message 3:
"Hmm, that didn't work either. Try sharing your date of birth in the format MM/DD/YYYY."

The messages play in order, so the end user will see a different prompt each time they provide an invalid response.

Instead of repeatedly receiving the same message, the chatbot gradually provides more guidance on what information is expected, helping users correct their mistakes.

I also used failure responses to handle situations where the chatbot could not collect a valid date of birth even after multiple attempts.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex2_a028bc8d2)

---

---
