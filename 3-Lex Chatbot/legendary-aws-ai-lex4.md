<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Save User Info with a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex4)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Save User Info with a Lex Chatbot

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex4_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is is a service for building conversational interfaces into any application using voice and text. 
Lex is useful because it does the hard work of "remembering" for us. It lets us build a smart chatbot that feels natural to talk to, without needing to write hundreds of lines of complicated code or set up expensive databases!

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to:
● Saved data: Used an output context tag to store the user's birthday in the bot's temporary memory.
● Locked the follow-up: Set an input context tag so the follow-up intent only triggers when that birthday is already saved.
● Carried over details: Used the shortcut #contextCheckBalance.dateOfBirth to auto-fill the birthday slot so the bot never asks twice.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how easily a mix-up between input and output context tags could break the bot. Setting the context tag as both an input and output on the CheckBalance intent completely locked it, preventing the bot from recognizing my initial requests.

### This project took me...

This project took me 2 hours to complete.

---

## Context Tags

Context tags are used to store and check for specific information across different parts of a conversation. They help save the user from having to repeat certain information.

There are two types of context tags:
● Input context tags
● Output context tags

I created a context tag called "contextCheckBalance".
This context tag was created in the intent of remembering the birthday of the user, saving them from having to repeat it especially within the same chat.
This tag stores information about 90 seconds or 5 turns in conversation.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex4_97dc2351)

---

## FollowUpCheckBalance

I created a new intent called FollowupCheckBalance. The purpose of this intent is to allow a follow-up balance check request from the user without requiring date of birth authentication.

FollowupCheckBalance intent is connected to the CheckBalance initent, because FollowupCheckBalance uses "contextCheckBalance" as its input context. By setting "#contextCheckBalance.dateOfBirth" as a default value, the followup intent can directly retrieve and reuse the saved birthday.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex4_12345678)

---

## Input Context Tag

"contextCheckBalance" was created as an output context in CheckBalance to save the user's session data. It connects to FollowupCheckBalance as an input context, acting as a key to unlock the intent and share that saved birthday data.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex4_c4fc89af)

---

## The final result!

To see the context tags and followup intent in action, I asked BankerBot to check the balance in my other account than the one I had asked before used phrases like the ones below defined in sample utterances:-
● How about my {accountType} account?
● What about {accountType} ?
● And in {accountType} ?


If I had gone straight to trying to trigger FollowUpCheckBalance without setting up any context the bot executes the FallBack intent.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex4_505be5b8)

---

## Managing context expiry

An extension for this project is to manage contextCheckBalance's context expiry, which means how long the bot will remember the information in this case the birthday of the user.
By default, expiry is in 5 turns or 90 seconds, whichever happens first.

I updated my bot's context expiry to 1 turn and 5 seconds. What this means for my end users is that they cannot check the balance for another account without refreshing the chat and providing the auhetication again...this is done to ensure privacy for user details to ensure nobody misuses it.

A long context expiry window would be helpful when you expect the user to have long conversations and run through multiple intents in the same session. 
A shorter context expiry window would be helpful when information is sensitive and you'd want to protect the user from attackers getting access to chat windows with lots of active contexts.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-ai-lex4_81b763822)

---

---
