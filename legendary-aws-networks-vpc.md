<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-vpc)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create an Amazon VPC, create a public subnet, and create an internet gateway. I'm doing this project because I wanted to understand how cloud networks are set up and how different AWS resources communicate inside a private environment.

### What is Amazon VPC?

Amazon VPC is Virtual Private Cloud and it is useful because it is an important must know AWS clous skill

In today's project, I used Amazon VPC to create a subnet and internet gateway

### Personal reflection

This project took me 1hr 30 mins

One thing I didn't expect in this project was the secret mission and how much it actually taught me

---

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I accessed the VPC console in AWS and created a new VPC because I wanted to understand how to build a private network where cloud resources like EC2 instances can be deployed and managed.

### How VPCs work

VPCs are useful because they allow you to create a private environment in the cloud. Inside a VPC, you can decide how resources communicate with each other and whether they should be accessible from the internet or remain private.
This gives better control over security and networking because everything can be organized inside this virtual network instead of being publicly exposed.

### Why there is a default VPC in AWS accounts

There was already a default VPC in my account when it was created. This exists so that users can start launching resources like EC2 instances immediately without needing to first learn how to configure networking.
If the default VPC didn’t exist, new users would have to create and configure a VPC before they could even start using many AWS services.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-networks-vpc_2facf927)

### Defining IPv4 CIDR blocks

To set up my VPC, I had to define an IPv4 CIDR block.
CIDR stands for Classless Inter-Domain Routing, and it basically defines the range of IP addresses available in the network.
An easy way to think about it is like defining the boundaries of a city. Inside that city, there will be smaller areas where different resources can exist.

---

## Subnets

### What I did in this step

In this step, I launched a subnet inside my VPC because a VPC is a large network space, and subnets help divide that space into smaller sections where different resources can run.
This helped me understand how networking inside AWS is structured.



### Creating and configuring subnets

Subnets are used to group resources based on their access level and purpose.
Some subnets are public, which means resources inside them can communicate with the internet. Other subnets are private, which means resources are restricted and cannot be accessed directly from the internet.
There were already subnets in my account for each Availability Zone in the region. I noticed that my region had three subnets, which means it has three availability zones.

### Public vs private subnets

The difference between public and private subnets is mainly about internet access.
A public subnet is connected to the internet, so resources inside it can communicate with external networks.
A private subnet does not have direct internet access and is usually used for internal services like databases that should not be publicly exposed.
For a subnet to be considered public, it must be connected to an internet gateway.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-networks-vpc_157c4219)

### Auto-assigning public IPv4 addresses

Once I created my subnet, I enabled auto-assign public IPv4 addresses.
This setting ensures that whenever an EC2 instance is launched inside the subnet, it automatically receives a public IP address.
This saves time because I don’t have to manually assign an IP address every time I launch a new instance.

---

## Internet gateways

### What I did in this step

In this step, I connected my VPC to the internet using an internet gateway because it acts like a bridge between my private network and the public internet.
This allows resources inside my VPC to communicate with external networks.


### Setting up internet gateways

Internet gateways are important because they make applications accessible from the internet.
Once an internet gateway is attached to a VPC, resources like EC2 instances with public IP addresses can communicate with users outside the network.
Without this step, the resources inside the VPC would remain private and would not be reachable from the internet.

Attaching an internet gateway to a VPC means resources in my VPC can now access the internet. The EC2 instances with public IP addresses also become accessible to users, so your applications hosted on those servers become public too. If I missed this step none of my resouces would be public and accessible by anyone.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

### What I'm doing in this extension

In this project extension, I will Open a handy tool (called AWS CloudShell) to run commands & Run AWS CLI commands to set up a VPC, subnet and internet gateway because it will enable me to know and learn better how VPC's work.

### Exploring CloudShell and CLI

VPC resources can also be created using CloudShell, which allows you to run commands directly inside the AWS environment.
The AWS CLI is a tool that lets you create, update, or delete AWS resources using commands instead of clicking through the console interface.
This gave me a better understanding of what is happening behind the scenes when resources are created.

### Debugging my setup

To set up a VPC or a subnet, you can use the command... Make sure to avoid errors by including...nnnn

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-networks-vpc_9b2465411)

### Comparing CloudShell vs AWS Console

Compared to using the AWS Console, using commands can help you understand in more detail how AWS resources are created and managed.
However, the console is easier to use because everything is visual and you can clearly see what is being configured.
Overall, for this project I preferred using the AWS Console, because it helped me understand the networking structure step by step.

---

---
