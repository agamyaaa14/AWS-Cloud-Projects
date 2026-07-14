<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Peering

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-peering)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## VPC Peering

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-peering_88727bef)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS. It is useful because it gives us complete control over our networking environment, allowing us to secure and control how our cloud resources communicate with each other.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create two completely separate virtual networks with unique IP CIDR blocks and securely connected them together using a private VPC Peering connection and updated route tables.

### One thing I didn't expect in this project was...

I didn't expect how adding just one extra rule in the route table can unblock traffic instantly, highlighting the critical importance of minor routing details and route table rules in resolving network communication blocks.

### This project took me...

This project took me 1 hour to complete.

---

## In the first part of my project...

### Step 1 - Set up my VPC

In this step I will create two VPCs super fast from scratch by using the visual VPC Resource Map.

### Step 2 - Create a Peering Connection

In this step, I will establish a connection between the VPCs I have created because we need to enable secure, private communication. 
This VPC peering connection lets our resources route traffic using private IP addresses, bypassing the public internet.

### Step 3 - Update Route Tables

In this step, I will update the route tables for both VPCs to target our peering connection. 
This is necessary because even though they are peered, they cannot communicate until we add routes directing traffic to each other's CIDR blocks.

### Step 4 - Launch EC2 Instances

In this step, I will launch an EC2 instance in each VPC, so that I can use them to test the VPC peering connection. 

---

## Multi-VPC Architecture

I started this project by launching two separate VPC networks. 
Within each VPC, I configured one Availability Zone, one public subnet, and zero private subnets. 
Additionally, the setup automatically created two route tables for each network: one default route table and one public route table.

The CIDR blocks for VPC 1 and VPC 2 are 10.1.0.0/16 and 10.2.0.0/16 respectively. 
These must be unique because overlapping IP address ranges would cause severe routing conflicts, preventing our resources from determining which private network to target during communication.

### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as we are using EC2 Instance Connect. 
This service automatically manages and pushes a temporary key pair for us behind the scenes, eliminating the need to manage .pem files manually.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-peering_11111111)

---

## VPC Peering

A VPC peering connection is a direct, private network connection between two VPCs. It allows resources in either VPC to communicate with each other securely using private IP addresses, acting as if they are on the same virtual network.

VPCs use peering connections to transfer data securely and directly without exposing traffic to the public internet. This improves security, reduces data transfer costs, and keeps communication entirely within the AWS global network.

The Requester is the VPC that initiates the peering connection by sending an invitation. 
The Accepter is the target VPC that must approve and accept the invitation. 
No traffic can flow until the Accepter approves the request.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-peering_1cbb1b88)

---

## Updating route tables

After accepting a peering connection, my VPCs' route tables need to be updated because resources in each network still do not know how to reach the other. 
We must define routing rules that map the target CIDR blocks to our peering connection.

In VPC 1, the new route destination was 10.2.0.0/16. 
In VPC 2, the new route destination was 10.1.0.0/16. 
The target for both routes was the newly established peering connection (VPC 1 <> VPC 2).

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-peering_4a9e8014)

---

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

In this step, I will use EC2 Instance Connect to connect to our EC2 instances because we need to verify they can access each other and troubleshoot any initial networking and connection errors.

### Step 6 - Connect to EC2 Instance 1

In this step, I will connect to our first EC2 instance and resolve any connection issues because we need to verify that our VPC security groups are configured to allow inbound SSH traffic from the internet.

### Step 7 - Test VPC Peering

In this step, I will use the ping command to send test messages from my first EC2 instance to the private IP of the second instance because we need to verify that our private VPC Peering connection is successfully routing traffic.

---

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect to securely connect to my EC2 instance directly from the browser. It allows me to access the command line of my server without needing to manually generate, download, or manage SSH key pairs.

I was stopped from using EC2 Instance Connect as the instance lacked a public IPv4 address. Because EC2 Instance Connect must connect over the public internet, it cannot reach an instance that only has a private network interface.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-peering_7685490c)

---

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are static, persistent public IPv4 addresses allocated to my AWS account. 
Unlike dynamic IPs, they do not change when the EC2 instance is stopped or restarted.

Associating an Elastic IP address resolved the error because it gave our instance a permanent public entrance point. This allowed AWS's public EC2 Instance Connect service to successfully locate and route SSH traffic to the instance.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-peering_45663498)

---

## Troubleshooting ping issues

To test VPC peering, I ran the command "ping" followed by the private IP address of my second EC2 instance (for example, ping 10.2.15.102) from the terminal of my first EC2 instance.

A successful ping test validates my VPC peering connection because it proves that private, two-way ICMP communication is successfully routing between the two isolated VPCs without exposing traffic to the public internet.

I had to update my second EC2 instance's security group because default settings block inbound ICMP traffic. I added a new rule allowing 'All ICMP - IPv4' from the source CIDR block of VPC 1 (10.1.0.0/16).

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-peering_7a29d352)

---

---
