<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use AWS IAM to control permissions and access inside my AWS account.

I'm doing this project to learn the basics of cloud security. In real companies, managing access permissions is extremely important, and there are even roles like IAM Engineers who specialize in this area.

### Tools and concepts

Services I used were Amazon EC2 and AWS IAM.

Key concepts I learnt include IAM users, policies, user groups, and account aliases.

I also learnt how JSON policies work and how the IAM Policy Simulator helps test permissions before applying them.

During this project I also practised launching EC2 instances, tagging instances, and logging into AWS using a different IAM user.

### Project reflection

This project took me approximately 2 hours.

The most challenging part was understanding IAM policies, especially because they are written in JSON and contain multiple statements.

The most rewarding moment was seeing a “permission denied” error when the intern tried to stop the production instance, which confirmed that the IAM policy was working correctly.

---

## Tags

### What I did in this step

In this step, I will launch two EC2 instances because we need to simulate separate development and production environments.

### Understanding tags

Tags are labels used to organize AWS resources. They help with resource management, cost tracking, and applying policies to specific resources.

### My tag configuration

The tag I’ve used on my EC2 instances is called Env.
The values I assigned to my instances were 'development' and 'production', which allowed me to differentiate between the two environments.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will use IAM policies to control the access of a new NextWork intern because they should only have access to the development environment and not the production environment.

### Understanding IAM policies

IAM policies are permission rules that define what actions users can or cannot perform on AWS resources.

These policies are attached to users, groups, or roles and determine what level of access each user has.

### The policy I set up

For this project, I set up a policy using JSON, which is the format AWS uses to define permission rules.

### Policy effect

The policy uses an Effect field that can either be Allow or Deny.

If a rule is set to Deny, it always takes priority over Allow.

In my policy, the first statement used Effect: Allow to permit certain actions.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes in a JSON policy define:
   ● Effect – whether the action is allowed or denied
   ● Action – what operation the user can perform
   ● Resource – which AWS resource the rule applies to

---

## My JSON Policy

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will simplify user login to my AWS account using an account alias because the intern should be able to log in easily while still having limited permissions.

### Understanding account aliases

An account alias is a friendly name for an AWS account that replaces the long numeric account ID when signing in.

### Setting up my account alias

Creating an account alias took me about 2 minutes.

Now my AWS console sign-in URL is:
https://nextwork-alias-agamyaaa14.signin.aws.amazon.com/console

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I will set up a dedicated IAM group for all NextWork interns because managing permissions at the group level is easier than assigning permissions to each user individually.

### Understanding user groups

IAM user groups are collections of users that share the same permissions.
Policies can be attached to the group so that every user in the group automatically receives the same access permissions.

### Attaching policies to user groups

I attached the policy I created to this user group, which means simplifying managing permissions and ensuring consistency across users who have similar access to AWS resources. 

### Understanding IAM users

IAM users are individual identities that represent people who need access to AWS resources, while user groups are used to organize and manage multiple users together.

---

## Logging in as an IAM User

### Sharing sign-in details

The first way is to email the sign-in instructions, and the second way is to share a CSV file that contains the login details and instructions.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that some dashboard sections showed “Access Denied.”

This happened because the intern was only given permissions for the development EC2 instance, and not for other resources.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will log into AWS using the intern's IAM user because I want to test whether the policy correctly restricts access to production resources.

### Testing policy actions

I tested my JSON IAM policy by attempting to stop both the development and production EC2 instances.

### Stopping the production instance

When I tried to stop the production instance, I received a “Failed to stop the instance” error message.

This happened because the intern was not given permission to modify the production environment.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, it stopped successfully.
This was because the intern was allowed to manage the development environment but not the production one.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

In this project extension, I'm going to use a tool called the IAM Policy Simulator.
I'm doing this because it helps test policies safely without affecting real AWS resources.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool that allows you to check whether a user has permission to perform certain actions before actually trying them.
It is useful for validating policies and troubleshooting permission issues.

### How I used the simulator

I set up a simulation for the actions DeleteTags and StopInstances.

The results initially showed Denied for both actions, which helped me understand how the policy rules were being applied.

I then adjusted the resource scope of the instances to make sure the policy applied correctly.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-security-iam_069d8a621)

---

---
