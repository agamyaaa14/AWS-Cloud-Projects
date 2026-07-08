<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-security)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is my isolated private network on AWS. It is useful because it gives me full control over my cloud environment, allowing me to secure workloads using custom subnets, gateways, route tables, and firewalls.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to build a secure network in us-east-1. I deployed a custom VPC and subnet, then configured route tables, security groups, and custom NACLs to isolate and control HTTP traffic flows.

### One thing I didn't expect in this project was...

One thing I didn't expect was how many elements control traffic flow. It made me realize that in networking, nothing happens by accident there is a logical reason behind every configuration, from route tables down to individual firewall rules.

### This project took me...

This project took me almost 2 hours.

---

## Route tables

Route tables are like GPS for the resources in the subnet. Just like how a GPS helps people get to their destination in a city, a route table is a table of rules, called routes, that decide where the data in our network should go.
Every subnet in our VPC needs to be linked to a route table, because the table tells your subnet's traffic where to travel to send and receive data.

Routes tables are needed to make a subnet public because it acts as a directory. Without an explicit rule mapping outgoing traffic to an Internet Gateway, my subnet has no path to the public internet and remains isolated.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Routes are defined by their destination and target, which mean–
Destination is the network IP range (CIDR block) where my traffic wants to go. 
Target is the specific gateway or connection resource used as the immediate next hop to get there.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 and a target of my custom Internet Gateway ID.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are stateful virtual firewalls that manage inbound and outbound traffic at the individual resource level, acting as an essential line of defense for my EC2 instances.

### Inbound vs Outbound rules

IInbound rules are filters controlling traffic allowed to enter my resources. I configured an inbound rule that allows HTTP traffic on Port 80 from anywhere (0.0.0.0/0), ensuring public users can access my web server.

Outbound rules are filters controlling traffic leaving my resources. By default, my security group's outbound rule allows all traffic to any destination, letting my web server request updates and send data freely.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are stateless, subnet-level firewalls. Operating at subnet boundaries, they inspect and filter all incoming and outgoing data packets against ordered rules to either allow or deny traffic.

### Security groups vs. network ACLs

Security groups are stateful firewalls controlling traffic at the resource level (like EC2). Network ACLs are stateless firewalls managing broader traffic at the subnet level, creating a layered defense-in-depth.

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, all default network ACLs allow all inbound and outbound traffic to flow freely across the subnets. This ensures immediate connectivity until custom, restrictive security rules are configured.

In contrast, a custom ACL’s inbound and outbound rules are automatically set to deny all traffic be default.
They block all communication entirely until I explicitly configure rule entries to allow specific traffic to pass through.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

I created additional VPC resources, subnets, and an internet gateway. Instead of my usual region, I used US East (N. Virginia). Teams would use multiple regions to ensure disaster recovery, high availability, and reduce latency for global users.

EC2 Global View is a tool where you can find VPC resources across all regions. I could even narrow down my search by resource type or tags. Without EC2 Global View, you'd have to switch regions manually to find forgotten or active resources.

Now that I've learnt about EC2 Global View, I'd use it again to audit my account across all AWS regions to instantly locate active EC2 instances or orphaned VPC resources, helping me prevent unexpected billing charges and maintain a secure, clean cloud environment.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-security_b03ea6162)

---

---
