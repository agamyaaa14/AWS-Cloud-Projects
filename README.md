# ☁️ AWS Cloud & Generative AI Portfolio

A collection of hands-on AWS projects completed through NextWork to strengthen my understanding of cloud computing, security, networking, and Generative AI applications.

These projects helped me move from basic AWS fundamentals to building AI-powered applications using Amazon Bedrock, Agents, Flows, Guardrails, and Foundation Models.

---

## 🚀 Projects

### 🌐 Cloud Fundamentals & Infrastructure

| Project                                 | Skills Demonstrated                                                      | Documentation                          |
| --------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------- |
| AWS Account Setup & Security            | AWS Account Management, MFA, Billing Alerts, Cloud Security Fundamentals | [View Project](./1-Cloud%20Fundamentals/legendary-aws-account-setup.md) |
| Host a Website on Amazon S3             | Amazon S3, Static Website Hosting, Bucket Policies, Access Control       | [View Project](./1-Cloud%20Fundamentals/legendary-aws-host-a-website-on-s3.md) |
| Cloud Security with AWS IAM             | IAM Users, Groups, Policies, Role-Based Access Control                   | [View Project](./1-Cloud%20Fundamentals/legendary-aws-security-iam.md) |
| Build a Virtual Private Cloud (VPC)     | VPC, Subnets, Internet Gateway, Networking Fundamentals                  | [View Project](./1-Cloud%20Fundamentals/legendary-aws-networks-vpc.md) |
| Join the Cloud Beginner Challenge       | Learning Path, Cloud Fundamentals, Practical Applications                | [View Project](./1-Cloud%20Fundamentals/legendary-aws-beginners-challenge.md) |


### 🤖 Amazon Bedrock & Generative AI

| Project                                 | Skills Demonstrated                                                      | Documentation                          |
| --------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------- |
| Build an AI Chatbot with Amazon Bedrock | Foundation Models, Converse API, Prompt Engineering, Guardrails          | [View Project](./2-AWS%20Bedrock%20GenAI/legendary-aws-genai-bedrock-chatbot.md) |
| AI Finance Agent with Amazon Bedrock    | Bedrock Agents, Code Interpreter, Agent Memory, Financial Analysis       | [View Project](./2-AWS%20Bedrock%20GenAI/legendary-aws-genai-bedrock-agent.md) |
| AI Email Router with Bedrock Flows      | Bedrock Flows, Prompt Management, Conditional Routing, Guardrails        | [View Project](./2-AWS%20Bedrock%20GenAI/legendary-aws-genai-bedrock-flows.md) |


### 🗣️ Amazon Lex Chatbot

| Project                                 | Skills Demonstrated                                                      | Documentation                          |
| --------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------- |
| Build an Amazon Lex Chatbot             | Amazon Lex fundamentals, NLU/ASR concepts, Conversation design, Project documentation | [View Project](./3-Lex%20Chatbot/legendary-aws-ai-lex.md) |
| Lex Chatbot — Multi-turn Flow           | Intent & utterance design, Fallback handling, Confidence tuning, Voice/text testing, IAM role configuration | [View Project](./3-Lex%20Chatbot/legendary-aws-ai-lex1.md) |
| Lex Bot Integrations & Testing          | Custom slot types, Slot filling & validation, Slot prompts/reprompts, Failure handling, Slot-linked intents | [View Project](./3-Lex%20Chatbot/legendary-aws-ai-lex2.md) |
| Connect Lex with Lambda                 | Lex ↔ Lambda integration, Aliases and versioning, Code hooks, Fulfilment, Backend logic for chatbots, Customizing Lambda responses | [View Project](./3-Lex%20Chatbot/legendary-aws-ai-lex3.md) |
| Save User Info with Lex Chatbot         | Output contexts, Input contexts, Session state management, Default slot values, Amazon Lex troubleshooting | [View Project](./3-Lex%20Chatbot/legendary-aws-ai-lex4.md) |
| Set Up Multiple Slots in a Lex Chatbot  | Shared slot types, Confirmation prompts, Visual builder design, AWS CloudFormation automation, Infrastructure as Code, Conversational flow logic, Transaction state validation | [View Project](./3-Lex%20Chatbot/legendary-aws-ai-lex5.md) |


### ☁️ Amazon VPC

| Project                                 | Skills Demonstrated                                                      | Documentation                          |
| --------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------- |
| Build a Virtual Private Cloud           | VPC creation, CIDR blocks, IPv4 addressing, Public subnet design, Internet Gateway configuration | [View Project](./4-VPC/1-legendary-aws-networks-vpc.md)      |
| VPC Traffic Flow and Security           | Route tables, Stateful Security Groups, Stateless Network ACLs, Cross-region resource management, EC2 Global View | [View Project](./4-VPC/2-legendary-aws-networks-security.md) |
| Creating a Private Subnet               | Private subnets, Non-overlapping IP routing, Isolated private route tables, Custom NACL firewalls, Defense in depth | [View Project](./4-VPC/3-legendary-aws-networks-privacy.md) |
| Launching VPC Resources                 | EC2 instance deployment (public & private), Key pair security, AWS VPC Resource Map, Automated VPC wizard configuration, Security group rule nesting | [View Project](./4-VPC/4-legendary-aws-networks-ec2.md) |
| Testing VPC Connectivity | SSH via EC2 Instance Connect, Cross-subnet ICMP (ping) verification, Security group and Network ACL (NACL) troubleshooting, Outbound web server testing with curl, HTTP 301 redirect analysis | [View Project](./4-VPC/5-legendary-aws-networks-connectivity.md) |
| VPC Peering | Multi-VPC architecture, CIDR planning, VPC Peering connection, Cross-VPC routing, Security group rules, ICMP (ping) testing | [View Project](./4-VPC/6-legendary-aws-networks-peering.md) |
| VPC Monitoring with Flow Logs | VPC Flow Logs configuration, CloudWatch Log Groups, IAM roles and policies, CloudWatch Logs Insights, log querying and analysis, traffic monitoring | [View Project](./4-VPC/7-legendary-aws-networks-monitoring.md) |



### 🗄️ Database Management & NoSQL

| Project                                 | Skills Demonstrated                                                      | Documentation                          |
| --------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------- |
| Load Data into DynamoDB                 | Amazon DynamoDB, AWS CLI, AWS CloudShell, JSON Data Loading, NoSQL Schemas, Console Management | [View Project](./5-Databases/1-aws-loaddata-dynamodb.md) |
| Query Data with DynamoDB                | Advanced Querying, Partition & Sort Keys, CLI Transactions, Consistency Controls, Data Filtering | [View Project](./5-Databases/2-aws-querydata-dynamodb.md) |
---


## 🛠️ AWS Services Explored

### Cloud Infrastructure & Networking
* **Amazon VPC** (Virtual Private Clouds, Subnets, Route Tables, Internet Gateways)
* **Amazon EC2** (Virtual Servers, Deployment Environments)
* **Amazon S3** (Simple Storage Service, Static Website Hosting, Bucket Policies)
* **EC2 Global View** (Cross-Region Resource Management)
* **AWS CloudShell** (Command Line Interface access)

### Security & Access Control
* **AWS IAM** (Identity and Access Management, Users, Groups, Custom Policies)
* **MFA** (Multi-Factor Authentication & Account Security)
* **Security Groups** (Stateful instance-level firewalls)
* **Network ACLs** (Stateless subnet-level firewalls, Public vs. Private custom NACLs)

### Generative AI & Intelligent Agents
* **Amazon Bedrock** (Foundation Models, Converse API)
* **Bedrock Agents** (Autonomous agent orchestration, memory preservation)
* **Bedrock Flows** (Visual workspace for AI workflow design)
* **Guardrails** (Safety, filter settings, responsible AI system design)
* **Code Interpreter** (Dynamically running code for data analysis)

### Conversational AI
* **Amazon Lex** (NLU, Conversational interface design, Slot types, Multi-turn flow)
* **AWS Lambda** (Serverless backend logic, custom fulfillment code hooks)

### Automation & Infrastructure as Code
* **AWS CloudFormation** (Automating resource deployment, Infrastructure as Code)

---

## 📚 Key Concepts Learned

### 1. Cloud Networking & Infrastructure
* **Subnet Design Architecture:** Designing non-overlapping CIDR blocks, isolating public and private subnets, and managing IPv4 address allocations.
* **Routing Rules & Traffic Management:** Configuring public route tables pointing to an Internet Gateway and isolating private route tables to block direct internet traffic.
* **Network Defense-in-Depth:** Deploying multi-layered security using stateful Security Groups (resource-level) and stateless custom Network ACLs (subnet-level) with deny-by-default logic.
* **Multi-Region Resource Visibility:** Navigating and managing distributed cloud infrastructure utilizing specialized tools like EC2 Global View.

### 2. Cloud Security & IAM Governance
* **Least Privilege Access:** Developing custom JSON policies to restrict access based on tags, environments (Dev/Prod), and user roles.
* **IAM Governance:** Structuring administrative controls by organizing users into specialized groups, configuring MFA, and setting up billing alarms for cost governance.
* **Object Storage Security:** Formulating Amazon S3 bucket policies to enable secure static website hosting while controlling access.

### 3. Conversational AI Design (Amazon Lex)
* **Conversational Engineering:** Modeling intent-utterance mappings, multi-turn dialogue configurations, fallback handling, and confidence score thresholds.
* **Data Capture & Session Management:** Designing custom slot types, enforcing slot validation prompts/reprompts, managing session persistence, and using input/output contexts to preserve user states across multi-turn flows.
* **Serverless Fulfillment:** Integrating chatbots with AWS Lambda backend hooks to dynamically process slot data, construct custom responses, and finalize transactions.

### 4. Generative AI & Workflow Orchestration
* **Autonomous Agent Architecture:** Building task-specific agents using Bedrock Agents, enabling context retention, and incorporating advanced capabilities like Code Interpreter for run-time data analysis.
* **Visual Workflow Design:** Designing robust AI processing flows with Bedrock Flows, prompt management systems, and conditional routing logic.
* **AI Safety & Moderation:** Implementing content filtering, safety checks, and enterprise rules using custom Guardrails to ensure responsible AI behaviors.
* **Trace-Based Debugging:** Reviewing model processing steps and tracing agent execution pathways to systematically optimize performance.

### 5. Cloud Automation & IaC
* **Infrastructure as Code (IaC):** Deploying repeatable, declarative templates using AWS CloudFormation to launch unified stacks containing conversational bots and IAM structures.
---

## 🎯 Learning Journey

I initially started exploring AWS to understand basic cloud concepts such as networking, storage, and security.

As I progressed, I began working with Amazon Bedrock and discovered how cloud infrastructure can be combined with Generative AI to build intelligent applications such as chatbots, finance agents, and email routers.

These projects represent my ongoing journey into Cloud Computing, Generative AI, and AI-powered application development.
