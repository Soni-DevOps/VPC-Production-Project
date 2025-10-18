# VPC-Production-Project

## About the project

This project emonstrates how to create a VPC that you can use for servers in prod env.

To improve resiliency, we eploy servers in 2 AZ by using an ASG and an ALB. For additional security, we deploy the servers in private subnets. The servers receive requests through the LB. The servers can connect to the internet using NAT gateway. To improve resiliency , you can deploy the NAT Gateway in both AZs.

## Architecture Overview

The VPC has public and private subnets in 2 AZs.
Each public subnet contains a NAT Gateway and a Load Balancer node.
The servers run in the private subnets, are launched and terminated by using an Auto Scaling Group, and receive traffic from the load balancer.

The servers can connect to the internet by using the NAT gateway.

## Project Overview:

1) Design and configure a VPC: Create a VPC with custom IP ranges. Set up public and private subnets. Configure route tables and associate subnets.

2) Implement network security: Set up network access control lists (ACLs) to control inbound and outbound traffic. Configure security groups for EC2 instances to allow specific ports and protocols.

3) Provision EC2 instances: Launch EC2 instances in both the public and private subnets. Configure security groups for the instances to allow necessary traffic. Create and assign IAM roles to the instances with appropriate permissions.

4) Networking and routing: Set up an internet gateway to allow internet access for instances in the public subnet. Configure NAT gateway or NAT instance to enable outbound internet access for instances in the private subnet. Create appropriate route tables and associate them with the subnets.

5) SSH key pair and access control: Generate an SSH key pair and securely store the private key. Configure the instances to allow SSH access only with the generated key pair. Implement IAM policies and roles to control access and permissions to AWS resources.

6) Test and validate the setup: SSH into the EC2 instances using the private key and verify connectivity. Test network connectivity between instances in different subnets. Validate security group rules and network ACL settings.

Screenshot of project:

# Key Definitions

### 1) Auto Scaling Group

An Auto Scaling Group is a collection of EC2 instances managed together according to specified scaling policies, minimum, maximum, and desired capacity settings. It automatically launches or terminates instances to maintain performance and optimize cost.

### 2) Load Balancer

A Load Balancer is a device or service that distributes incoming network or application traffic across multiple servers (or instances) to ensure no single server is overwhelmed, improving availability, performance, and reliability.

### 3) Target Group

A Target Group is an AWS resource that routes requests from a Load Balancer to one or more registered targets, such as EC2 instances, IP addresses, or Lambda functions, based on defined rules and health checks.

### 4) Bastion Host or Jump Server

A Bastion Host is a special-purpose instance placed in a public subnet that acts as a gateway for administrators to securely access resources (like EC2 instances) in private subnets using SSH or RDP.

### 5) VPC

A Virtual Private Cloud (VPC) is a logically isolated section of the AWS Cloud that allows you to define and control your own network configuration, including IP address ranges, subnets, route tables, and security settings.

### 6) Availability Zone

An Availability Zone is one or more discrete data centers within an AWS region, each with redundant power, networking, and connectivity, enabling high availability and fault tolerance for applications.

### 7) Subnets

A Subnet (subnetwork) is a segment of a VPC’s IP address space where you can launch AWS resources such as EC2 instances. Each subnet resides entirely within one Availability Zone.

### 8) Internet Gatway

An Internet Gateway is a horizontally scaled, redundant, and highly available AWS component that enables instances in a VPC to connect to the Internet and allows incoming traffic from the Internet to reach those instances (if permitted by security rules).

### 9) Security Group

A Security Group acts as a stateful firewall for your instances, allowing you to define rules that specify which traffic is allowed to enter (inbound) or leave (outbound) the instance.

### 10) NAT Gateway

A NAT (Network Address Translation) Gateway allows outbound-only Internet connectivity for resources in private subnets, translating private IP addresses to a public IP for communication with the Internet, while keeping the private subnet secure from incoming Internet traffic.








