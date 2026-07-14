<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Testing VPC Connectivity

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-connectivity)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

## Testing VPC Connectivity

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-connectivity_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a private virtual network in the AWS cloud. It is useful because it lets me isolate my cloud resources, control who can access them, and secure my applications from unauthorized traffic.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to test network connectivity. I used tools like ping to check communication between my public and private subnets, and curl to verify that my public server could reach the internet.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how precise networking has to be. Even a minute network setting, like a single rule in a security group or Network ACL, will completely block communication. Getting everything correct is incredibly crucial.

### This project took me...

This project took me about 60 minutes, including learning how to troubleshoot the network, understand terminal outputs, and configure my resources!

---

## Connecting to an EC2 Instance

Connectivity is all about how successfully different components in your cloud architecture can talk to each other and exchange data with external networks (such as the public internet). It is the backbone of any application because without connectivity, your servers cannot receive requests or send responses.

I was trying to connect to the "Agamya Public Server" using EC2 Instance Connect to test whether my public subnet resources are reachable from the AWS console.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-connectivity_88727bef)

---

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is a secure, browser-based service that lets me connect to my EC2 instances directly from the AWS Management Console using SSH, without needing to manually generate or store local SSH keys.

My first attempt at getting direct access to my public server resulted in an error, because the associated security group was only configured to allow inbound HTTP traffic (port 80). It did not have a rule allowing SSH traffic (port 22) from the internet.

I fixed this error by editing the inbound rules of my public security group to add a new rule allowing SSH traffic on port 22, setting the source to Anywhere-IPv4 so that EC2 Instance Connect's range of IP addresses could reach the server.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-connectivity_1cbb1b88)

---

## Connectivity Between Servers

Ping is a standard command-line utility used to test the reachability of a host on an IP network. 
I used ping to test the connectivity between my public server (the source) and my private server (the target) over their private IP addresses within our custom VPC.

The ping command I ran was "ping [Private IP of Private Server]" inside the terminal session of my public server (for example: ping 10.0.1.50).

The first ping returned no response and the terminal hung without showing any successful replies. 
This meant that while the servers are in the same VPC, a firewall rule or security group rule was blocking the ICMP packets from reaching the private server or preventing the private server from sending replies back.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-connectivity_defghijk)

---

## Troubleshooting Connectivity

I troubleshooted this by heading to my EC2 console and editing the inbound rules of my private security group. I added a rule to allow "All ICMP - IPv4" traffic, setting the source to my public security group ID so that only my public server is permitted to run ping tests against it.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-connectivity_4a9e8014)

---

## Connectivity to the Internet

Curl is a command-line tool used to transfer data to or from a server over various network protocols. It allows us to retrieve and download data, such as the raw HTML of a website, directly inside our terminal session.

I used curl to test the connectivity between my public server inside my VPC and external servers on the public internet, verifying that outbound routing and web traffic translation are working seamlessly.

### Ping vs Curl

Ping and curl are different because ping only checks if a target server is reachable by sending ICMP echo requests, while curl actually transfers data (like raw webpage files) to and from the server over protocols like HTTP or HTTPS.

---

## Connectivity to the Internet

I ran the curl command "curl example.com" which returned the raw HTML content of the Example Domain home page, showing that the request was processed and returned successfully.

![Image](http://nextwork.ai/happy_azure_swift_duck/uploads/aws-networks-connectivity_8ee57662)

---
