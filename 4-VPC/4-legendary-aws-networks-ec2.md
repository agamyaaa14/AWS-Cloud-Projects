<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-ec2)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Launching VPC Resources

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a secure, logically isolated virtual network that I can launch within my AWS account, and it is useful because it gives me total control over my custom network architecture, allowing me to choose my own IP address ranges, set up secure boundaries, and define exactly how traffic flows.

### How I used Amazon VPC in this project

I used Amazon VPC to deploy a custom network (my Agamya VPC) featuring a public subnet and a private subnet so that I could launch, connect, and isolate multiple EC2 instances based on their specific security needs.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how you can use the VPC resource map to quickly create a complete network that took me about three projects to build! In my mind, I was always wondering how the network actually looked. Even though there were static images guiding me, seeing the live, interactive VPC resource map provided by AWS made everything click. It was amazing to see how easily we can create and view connections between subnets, route tables, and gateways on a single page.

### This project took me...

This project took me almost 2 hours of hands-on build, review, and documentation time.

---

## Setting Up Direct VM Access

Directly accessing a virtual machine means logging directly into its operating system or terminal over the internet as if the machine were sitting right in front of me. This level of access is essential because it allows me to perform administrative tasks, install software, and run scripts directly on my public server, which cannot be done through the standard AWS Management Console.

### SSH is a key method for directly accessing a VM

SSH traffic means Secure Shell communication, which is a highly secure, encrypted type of network traffic used to remotely access and manage virtual servers. When I establish an SSH connection to my EC2 instance, all data, commands, and login credentials sent back and forth are encrypted so that nobody can intercept them over the internet.

### To enable direct access, I set up key pairs

Key pairs are a secure authentication method consisting of a public key that AWS installs on my virtual machine and a private key that I download and keep safe. They act like a digital lock and key, ensuring that only someone holding my matching private key can securely log into my EC2 instance.

A private key's file format means the specific file layout and encoding used to save the cryptographic key so that different systems can process it. My private key's file format was .pem (Privacy Enhanced Mail), which is the standard, highly compatible format supported by Linux and various other server types in AWS.

---

## Launching a public server

I had to change my EC2 instances' networking settings by opening the network settings editor during launch to move the server out of the default VPC. I selected my custom Agamya VPC, associated it with the Agamya Public Subnet, enabled the Auto-assign public IP option, and attached the pre-configured Agamya Public Security Group to control the incoming traffic.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because it requires a completely different, much stricter security than my public server. While my public server is designed to allow web traffic from the open internet, my private server needs to be isolated from the outside world and only accept highly restricted administrative connections.

My private server's security group's source is the Agamya Public Security Group, which means that only resources associated with that specific public security group (like my public EC2 instance) are allowed to communicate with my private server. Instead of allowing any random IP address on the internet to attempt to connect to my private server, I have restricted access to only a small, trusted group of my own resources.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC! This time, I selected the VPC and more option instead of "VPC only". This allowed me to automatically generate my entire VPC infrastructure—including subnets, route tables, and gateways—simultaneously on a single page, rather than jumping back and forth to create them individually.

A VPC resource map is a visual flow diagram that shows the architectural layout of a VPC at a glance. It displays how many subnets are being created, which ones are public or private, and exactly how they connect to different route tables and network gateways, making it much easier to inspect and manage the network.

My new VPC has a CIDR block of 10.0.0.0/16. It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC because AWS VPCs are logically isolated networks by default. Since they are completely separate sandboxes within my account, they will not cause IP conflicts unless I explicitly try to connect them later using a VPC peering connection.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options: 0 or 2. This was because the AWS wizard automatically builds in best practices for high availability and redundancy. Since I selected 2 Availability Zones, the wizard requires a public subnet in each zone to ensure my public-facing resources remain accessible even if an entire AZ goes offline.

The set up page also offered to create NAT gateways, which are network translation services that allow resources residing inside a private subnet to securely make outbound connections to the internet (for downloading software updates and patches) while completely blocking any inbound traffic from initiating connections from the outside world.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-ec2_8ee57662)

---

---
