<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# AI Email Router with Bedrock Flows

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-genai-bedrock-flows)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

---

## Introducing Today's Project!

Today I am building an AI-powered email routing system using Amazon Bedrock.

The goal of this project is to automatically analyze customer emails, identify their intent, and generate an appropriate response. Instead of manually sorting emails, the workflow uses AI to classify messages and route them to the correct response path.

### Key tools and concepts

### Challenges and wins

---

## Navigating Amazon Bedrock

In this step, I am getting ready to build by signing into my AWS account, selecting the correct region, and confirming that Amazon Nova Lite is available in Amazon Bedrock.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_f3j8w2n5)

---

## Creating the Classifier Prompt

In this step, I am creating:
● A classifier prompt that categorizes emails by intent
● Test emails to verify the classification
● A versioned prompt that can be reused in workflows

These are important because prompt templates allow AI instructions to be reused consistently across different applications.

### Understanding the classifier prompt

This prompt tells the AI to:
● Read a customer email
● Decide whether it is a complaint, question, or refund request
● Return only the classification label in lowercase

This ensures that the output remains predictable and can be used by other parts of the workflow.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_x9m3t6k1)

### How the classifier works

When I tested the classifier, it correctly returned outputs such as complaint, question, or refund.

The output format is important because the routing logic depends on exact matches. For example, "complaint" and "Complaint" would be treated differently by the flow, so consistency is critical.

---

## Building the Response Prompt Library

In this step, I am creating:
● A complaint response prompt with an empathetic tone
● A general-purpose response prompt
● A reusable prompt library for different email scenarios

We need separate prompts because, different customer situations require different communication styles.
Complaint emails need empathy and reassurance, while general questions or refund requests require a more professional and informative response.
Using separate prompts helps the AI generate responses that are better suited to the customer's intent.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_y2j8b4w6)

---

## Building the Email Router Flow

In this step, I am building:
● A Bedrock Flow using the classifier prompt
● A condition node for routing decisions
● Response nodes that generate the final email reply

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_w3x8n5q2)

### How the classifier routes emails

The classifier produces an output called 'modelCompletion', which contains the classification result.

This output is passed to the condition node, which evaluates the result and determines which response path should be followed.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_h4y2c8f6)

### Completing the flow architecture

The workflow starts with a customer email entering the flow.

The email is first analyzed by the classifier prompt, which determines whether the email is a complaint, question, or refund request.

The classification result is then passed to a condition node, which routes complaint emails to the complaint-response prompt, while all other emails follow the general-response path.

This helped me understand how AI workflows can combine prompts and decision-making logic to automate business processes.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_a5d3g7k1)

---

## Testing and Debugging the Flow

In this step, I am testing:
● Whether the flow correctly classifies emails
● Whether routing works as expected
● How to debug workflows using traces

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_p4w8n1y6)

### Tracing the email routing path

When I tested a complaint email, the classifier correctly identified it as a complaint.

The condition node then routed the email to the complaint-response branch, where the AI generated an empathetic customer support response based on the instructions I had configured.

Using traces allowed me to see exactly how the data moved through each stage of the workflow.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_v6b1c8f4)

### How default routing works

The question email reached the general-response branch because I only created an explicit condition for complaints.

Any email that does not satisfy that condition automatically follows the default route, which is connected to the general-purpose response prompt.

This showed me how fallback logic works inside Bedrock Flows.

---

## Adding Content Safety with Guardrails

### Configuring content filters

I enabled harmful content filtering using Bedrock Guardrails.
These filters help detect and block inappropriate, abusive, or unsafe content before it reaches the classification stage.

Filtering is important because it prevents the workflow from processing harmful inputs and helps maintain safe AI interactions.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_v8km3q2x)

### Normal vs. harmful email behavior

When I sent a normal customer email, the workflow processed it successfully and generated an appropriate response.

When I sent a harmful email, the guardrail intercepted it and returned the configured safety message:
"This email contains content that cannot be processed."

This demonstrated how guardrails act as an additional safety layer before the AI workflow executes.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_j6yd2m8k)

### Testing the guardrail

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-genai-bedrock-flows_w3bp5n1f)

---

## Wrapping Up

The key tools I used include:
● Amazon Bedrock
● Bedrock Flows
● Bedrock Prompt Management
● Amazon Nova Lite
● Bedrock Guardrails

Key concepts I learned include:
● Prompt engineering and prompt versioning
● Building reusable prompt templates
● Using prompt variables such as {{email}}
● Designing visual AI workflows
● Conditional routing based on AI outputs
● Debugging workflows with traces
● Implementing content safety using guardrails

### Time and effort

This project took me approximately 2 hours.

The most challenging part was working with the visual flow builder on a smaller laptop screen, since it was sometimes difficult to view the entire workflow at once.

The most rewarding part was seeing the complete workflow successfully classify emails and automatically generate different responses based on customer intent.

### What's next

I completed this project to learn how AI workflows can be built using visual tools instead of traditional programming.

It also helped me understand how multiple AI components such as prompts, routing logic, and guardrails can work together in a real-world application.

The next skill I would like to learn is building more advanced AI systems that combine multiple agents and external tools to handle complex business tasks.

---

---
