<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Creating a Private Subnet

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-private)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Creating a Private Subnet

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-private_afe1fdbd)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is like our own isolated digital city inside the AWS cloud. It is useful because it lets us divide our network into public neighborhoods (for web servers) and private neighborhoods (for databases), keeping our most sensitive resources fully hidden and safe from the public internet.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a secure, isolated private subnet. I then configured a dedicated route table and a custom Network ACL to block all internet traffic and secure its boundaries.

### One thing I didn't expect in this project was...

One thing I didn't expect is how AWS automatically associates newly created subnets with existing resources by default. 
Because of this default behavior, my new private subnet was immediately linked to the main route table which was already connected to the Internet Gateway-highlighting how critical it is to manually isolate your resources.

### This project took me...

This project took me 1 hour 15 mins to complete and fully document.

---

## Private vs Public Subnets

The difference between public and private subnets is that a public subnet is directly connected to the internet through an Internet Gateway, meaning resources inside it can easily talk to the outside world. 
On the other hand, a private subnet has no direct pathway to the internet, keeping its resources fully isolated and hidden from external public access. 

Having private subnets are useful because they act as a secure, backend environment for most sensitive resources (like customer databases or backend application code). 
By keeping these systems in a private subnet, we can protect them from direct internet-based cyber attacks while still allowing them to communicate securely with the public-facing web servers.

My private and public subnets cannot have the same CIDR block(or overlapping range of IP addresses). 
Just like two physical houses in a city cannot share the exact same mailing address, every subnet in your VPC must have its own unique address range so that network traffic can be routed correctly without any confusion or conflict.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-private_afe1fdbd)

---

## A dedicated route table

By default, my private subnet is associated with the main route table of my VPC (initially named Agamya route table), which AWS automatically assigns to any new subnet that does not have an explicit association.

I had to set up a new route table because the main default table contains an active route pointing directly to the Internet Gateway. If I left my private subnet associated with it, the subnet would inherit this pathway and become public, exposing our backend resources to the internet.

My private subnet's dedicated route table only has one inbound and one outbound rule that allows strictly internal VPC traffic. This ensures resources within this subnet can communicate internally with other subnets in the VPC, but cannot send or receive any traffic to or from the public internet.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-private_b4b904b5)

---

## A new network ACL

By default, my private subnet is associated with the default Network ACL of my VPC (which displays as a hyphen "-" in the console's Name column because AWS creates it automatically behind the scenes without a name tag).

I set up a dedicated network ACL for my private subnet because the default network ACL is highly permissive, allowing all inbound and outbound traffic. Creating a custom, restricted NACL establishes a crucial firewall at the subnet boundary, ensuring defense in depth even if other resources in the VPC are compromised.

My new network ACL has two simple rules—
one inbound rule and one outbound rule (both marked with an asterisk *)—that deny all traffic by default. 

This completely isolates the private subnet from external and internal traffic until we explicitly configure rules to allow it.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-private_1ed2cb07)

---

---
