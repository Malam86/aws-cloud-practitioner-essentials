Module 5: Networking on AWS
🌐 Introduction to AWS Networking
🏠 Amazon VPC (Virtual Private Cloud)
Meaning: A virtual network dedicated to your AWS account that provides complete control over your virtual networking environment.

Key Concept: Your own private, isolated section of the AWS cloud where you can launch AWS resources in a virtual network you define.

Basic VPC Components:

VPC: The overall network container

Subnets: Segments of the VPC IP address range

Route Tables: Control traffic routing between subnets

Internet Gateway: Connect VPC to the internet

NAT Gateway: Allow private subnets to access internet

🏗️ VPC Fundamentals
IP Addressing and CIDR Blocks
Meaning: Classless Inter-Domain Routing (CIDR) blocks define the IP address range for your VPC.

Common CIDR Ranges:

10.0.0.0/16: 65,536 IP addresses (10.0.0.0 - 10.0.255.255)

172.16.0.0/16: 65,536 IP addresses

192.168.0.0/16: 65,536 IP addresses

Example VPC Setup:

text
VPC: 10.0.0.0/16
├── Public Subnet: 10.0.1.0/24 (256 addresses)
├── Private Subnet: 10.0.2.0/24 (256 addresses)
└── Database Subnet: 10.0.3.0/24 (256 addresses)
Subnets and Availability Zones
Meaning: Subnets are segments of your VPC's IP address range that you can place in different Availability Zones for high availability.

Subnet Types:

Public Subnets: Have route to internet gateway

Private Subnets: No direct internet access

Database Subnets: Isolated subnets for databases

Real-World Example: Three-Tier Application

text
VPC: 10.0.0.0/16
├── Public Subnets (Web Tier):
│   ├── 10.0.1.0/24 (us-east-1a)
│   └── 10.0.2.0/24 (us-east-1b)
├── Private Subnets (App Tier):
│   ├── 10.0.3.0/24 (us-east-1a)
│   └── 10.0.4.0/24 (us-east-1b)
└── Database Subnets (Data Tier):
    ├── 10.0.5.0/24 (us-east-1a)
    └── 10.0.6.0/24 (us-east-1b)
🛡️ Security in AWS Networking
Security Groups
Meaning: Virtual firewalls for your EC2 instances that control inbound and outbound traffic at the instance level.

Key Characteristics:

Stateful: Return traffic is automatically allowed

Instance-level: Applied to individual instances

Allow rules only: You can only specify what is allowed

Evaluate all rules: All rules are evaluated before deciding to allow traffic

Example Security Group Configuration:

yaml
WebServer Security Group:
  Inbound Rules:
    - HTTP (port 80) from 0.0.0.0/0
    - HTTPS (port 443) from 0.0.0.0/0
    - SSH (port 22) from 10.0.0.0/16
  Outbound Rules:
    - All traffic to 0.0.0.0/0
Network Access Control Lists (NACLs)
Meaning: Optional layer of security that acts as a firewall for controlling traffic in and out of subnets.

Key Characteristics:

Stateless: Return traffic must be explicitly allowed

Subnet-level: Applied to entire subnets

Allow/Deny rules: Can explicitly allow or deny traffic

Rule numbers: Processed in order from lowest to highest

Example NACL Configuration:

yaml
Public Subnet NACL:
  Inbound Rules:
    - Rule 100: Allow HTTP from 0.0.0.0/0
    - Rule 200: Allow HTTPS from 0.0.0.0/0
    - Rule 300: Allow SSH from corporate IP
    - Rule 400: Deny all traffic
  Outbound Rules:
    - Rule 100: Allow all traffic to 0.0.0.0/0
🔄 Network Traffic Flow
Internet Gateway (IGW)
Meaning: A horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet.

Use Cases:

Public web servers

Load balancers

NAT instances

NAT Gateway
Meaning: A highly available, managed Network Address Translation (NAT) service for your private subnets to access the internet while remaining private.

Use Cases:

Private instances needing software updates

Applications requiring external API access

Database servers needing security patches

Real-World Traffic Flow:
text
Internet User → Internet Gateway → 
Public Subnet (Load Balancer) → 
Private Subnet (Application Servers) → 
Database Subnet (Database) → 
NAT Gateway (for external API calls)
🌉 Advanced Networking Concepts
VPC Peering
Meaning: A networking connection between two VPCs that enables routing traffic between them using private IP addresses.

Use Cases:

Connecting development and production VPCs

Multi-account architectures

Shared services VPC

Example:

text
VPC A (10.0.0.0/16) ↔ VPC Peering Connection ↔ VPC B (10.1.0.0/16)
VPC Endpoints
Meaning: Enables private connectivity to AWS services from within your VPC without using an internet gateway, NAT device, VPN connection, or AWS Direct Connect.

Types:

Interface Endpoints: ENI with private IP

Gateway Endpoints: Route table entry (S3, DynamoDB)

AWS PrivateLink
Meaning: Provides private connectivity between VPCs and services hosted on AWS or on-premises, without exposing data to the public internet.

🚀 Network Services
Elastic Load Balancing (ELB)
Types:

Application Load Balancer (ALB): Layer 7, HTTP/HTTPS

Network Load Balancer (NLB): Layer 4, TCP/UDP

Classic Load Balancer (CLB): Legacy, both Layer 4 and 7

Amazon Route 53
DNS Services:

Domain registration

DNS routing

Health checking

Traffic flow

AWS CloudFront
Content Delivery:

Global edge locations

Content caching

DDoS protection

💰 Cost Optimization
Networking Cost Considerations:
Data Transfer: Costs between regions, AZs, and internet

NAT Gateway: Hourly charges + data processing

VPC Peering: Data transfer costs

PrivateLink: Hourly endpoint charges + data processing

Cost-Saving Strategies:
Use same AZ for high traffic between resources

Use CloudFront to reduce data transfer costs

Implement caching strategies

Choose appropriate load balancer types

🧪 Hands-On Practice
Created custom VPC with public and private subnets

Configured security groups and NACLs

Set up internet gateway and NAT gateway

Implemented route tables for proper traffic routing

✅ Completed on: [Insert Date]
