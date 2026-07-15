<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Monitoring with Flow Logs

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-monitoring)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## VPC Monitoring with Flow Logs

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_3e1e79a1)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a service that lets me launch AWS resources in a logically isolated virtual network that I define. It is useful because it gives me complete control over my network environment, including custom IP address ranges, subnets, route tables, and security firewalls, ensuring my cloud infrastructure is highly secure.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to deploy two separate virtual networks, establish an active VPC peering connection between them, configure custom route tables to allow private traffic, and set up VPC Flow Logs to capture real-time IP packets moving across my public subnet.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the recent CloudWatch console layout update. Adapting to the new Log Analytics dashboard layout was unexpected, but manually running my top byte transfer query and seeing my real-time ping data show up in the results was an incredibly rewarding experience!

### This project took me...

This project took me 2 hours.

---

## In the first part of my project...

### Step 1 - Set up VPCs

In this step, I will set up new VPCs from scratch using VPC Resource Map. 

### Step 2 - Launch EC2 instances

In this step, I will launch an EC2 instance in each VPC, so that I can use them to test the VPC peering connection. 

### Step 3 - Set up Logs

In this step, I will set up VPC Flow Logs on my public subnet and create a CloudWatch log group. 
I am doing this because we need Flow Logs to capture all the inbound and outbound network traffic data, and we need the log group to act as a secure folder to store those records so we can inspect them later.

### Step 4 - Set IAM permissions for Logs

In this step, I will create an IAM policy and role for VPC Flow Logs. 
This is because VPC Flow Logs does not have permission to send logs to CloudWatch by default, so we need to grant it explicit permissions to write and deliver our network traffic records.

---

## Multi-VPC Architecture

I started this project by launching two separate VPC networks. 
Within each VPC, I configured one Availability Zone, one public subnet, and zero private subnets. 
Additionally, the setup automatically created two route tables for each network: one default route table and one public route table.

The CIDR blocks for VPC 1 and VPC 2 are 10.1.0.0/16 and 10.2.0.0/16 respectively. 
These must be unique because overlapping IP address ranges would cause severe routing conflicts, preventing our resources from determining which private network to target during communication.

### I also launched EC2 instances in each subnet

My EC2 instances' security groups allow inbound ICMP traffic from all IP addresses (0.0.0.0/0). 
This is because we need both instances to accept ping requests from each other over our peered connection. Opening the source to 0.0.0.0/0 guarantees that the incoming ping packets originating from the other VPC are allowed through to verify connectivity.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_e7fa8775)

---

## Logs

Logs are like a diary for our computer systems. They record everything that happens, from users logging in to errors popping up. It's the go-to place to understand what's going on with systems, troubleshoot problems, and keep an eye on who’s doing what.

Log group is a big folder in AWS where we can keep related logs together. 
Usually, logs from the same source or application will go into the same log group, but logs are also region-specific. This means log data gets created and saved in the region it was created.

### I also set up a flow log for VPC 1

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_e8398869)

---

## IAM Policy and Roles

I created an IAM policy because VPC Flow Logs does not have permission by default to write logs to Amazon CloudWatch. This policy explicitly grants the permissions needed to create log groups, create log streams, and upload our network traffic data so we can monitor our VPC.

I also created an IAM role because AWS policies cannot be assigned directly to services. We must create an IAM role (the active identity) with our policy attached, and then assign that role to VPC Flow Logs so it has the authorization to write to CloudWatch.

A custom trust policy is a special policy that defines exactly who is allowed to use (or assume) an IAM role. 
It acts like a strict VIP list, ensuring that only the specific service we name - VPC Flow Logs - can use this role, keeping our account highly secure.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_4334d777)

---

## In the second part of my project...

### Step 5 - Ping testing and troubleshooting

In this step, I will connect to my instance in VPC 1 and try to send a ping command to my instance in VPC 2 using its private IP address. 
I'm doing this because we need to generate real network traffic for our Flow Logs to capture, and it also lets us test if our VPC peering connection is working.

### Step 6 - Set up a peering connection

In this step, I will set up a peering connection between the two VPCs because right now they cannot communicate with each other via the private network address.

### Step 7 - Analyze flow logs

In this step, I will query and analyze my VPC Flow Logs using CloudWatch Logs Insights. I am doing this because I want to inspect my network's traffic records, identify which IP addresses are sending the most data, and confirm that my VPC peering connection is successfully routing my private traffic.

---

## Connectivity troubleshooting

My first ping test between my EC2 instances had no replies, which means that there is currently no active connection or route between VPC 1 and VPC 2 for private traffic. 
Even though our security groups allow ping traffic, our network doesn't know how to route packets using private IP addresses yet.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_99d4ba42)

I could receive ping replies if I ran the ping test using the other instance's public IP address, which means that the target instance is online and its security group is successfully allowing ICMP traffic. 
However, this means the traffic is traveling over the public internet rather than the secure, private VPC peering connection.

---

## Connectivity troubleshooting

Looking at VPC 1's route table, I identified that the ping test with Instance 2's private address failed because there is no route directing traffic to VPC 2's network range. 
While my route table has a route to the internet, it is missing a direct route that points private traffic to my VPC peering connection.

### To solve this, I set up a peering connection between my VPCs

I also updated both VPCs' route tables so that any network traffic leaving VPC 1 destined for VPC 2's IP range (10.2.0.0/16) is sent directly to my peering connection, and any return traffic from VPC 2 is guided back to VPC 1's range (10.1.0.0/16) through the same connection.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_7316a13d)

---

## Connectivity troubleshooting

I received ping replies from Instance 2's private IP address! This means my VPC peering connection is active and my route tables are successfully directing private traffic. 
It also proves that my security groups are allowing ICMP traffic over my private network, confirming that my instances can communicate securely without sending data over the public internet.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_4ec7821f)

---

## Analyzing flow logs

Flow logs tell me about the metadata of IP traffic moving through my network interfaces. 
A standard flow log record is broken down into several parts: the version, the AWS account ID, the specific network interface ID, the source and destination IP addresses, the source and destination port numbers, the protocol number, the total number of packets and bytes, the start and end times, and whether the traffic was ALLOWED or REJECTED.

For example, the flow log I've captured tells me that a successful private connection occurred between my two EC2 instances. 
It displays the source IP address of my initiating instance in VPC 1, the destination IP address of my target instance in VPC 2, protocol number 1 (which represents my ICMP ping traffic), and a status of ACCEPT, proving my security groups and routes worked perfectly.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_d116818e)

---

## Logs Insights

Logs Insights is an interactive query tool in CloudWatch that allows me to search, filter, and analyze my log data. It helps me make sense of massive volumes of raw log streams by using specific query commands to group information, extract trends, and quickly troubleshoot network behaviors.

I ran the query that finds the top 10 byte transfers by source and destination IP addresses. 
This query analyzes my VPC Flow Logs in CloudWatch to identify which specific pairs of IP addresses in my network have sent and received the largest volumes of data, helping me easily spot the busiest communication paths.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-monitoring_3e1e79a1)

---

---
