# Module 5: Networking on AWS

## 🔌 Introduction to Networking Components

### 🏠 Amazon Virtual Private Cloud (Amazon VPC)
**Meaning:** A virtual network dedicated to your AWS account that provides complete isolation and control over your networking environment. It's logically isolated from other virtual networks in the AWS Cloud.

**Key Concept:** Think of VPC as your own private section of the AWS cloud - like having your own personal data center within AWS.

**Real-World Example: Company Office Building**

Traditional Office Building vs AWS VPC:
├── Office Building │ ├── AWS VPC
│ ├── Security Guards │ │ ├── Security Groups & NACLs
│ ├── Private Offices │ │ ├── Private Subnets
│ ├── Reception Area │ │ ├── Public Subnets
│ ├── Internal Hallways │ │ ├── Route Tables
│ └── Building Entrance │ │ └── Internet Gateway

**Technical Example: E-commerce Application VPC**

Company: "ShopEasy" E-commerce Platform
VPC: shopeasy-vpc (10.0.0.0/16)
├── Contains: Web servers, application servers, databases
├── Isolation: Completely separate from other AWS customers
├── Control: Full control over IP ranges, subnets, routing
└── Security: Custom security groups and network ACLs

### 🌐 Subnets
**Meaning:** A range of IP addresses in your VPC that you can launch AWS resources into. Subnets allow you to segment your network for security and organization.

**Key Concept:** Subnets divide your VPC into smaller, manageable network segments, typically placed in different Availability Zones for high availability.

**Real-World Example: Office Building Floor Plan**

Office Building Floor Plan vs VPC Subnets:
├── Office Floor Plan │ ├── VPC Subnet Design
│ ├── Public Areas │ │ ├── Public Subnets
│ │ └── Reception │ │ │ └── Web servers
│ ├── Work Areas │ │ ├── Private Subnets
│ │ └── Employee desks │ │ │ └── App servers
│ └── Secure Areas │ │ ├── Isolated Subnets
│ └── Server room │ │ │ └── Databases

**Technical Example: Three-Tier Application Subnets**

VPC: 10.0.0.0/16
├── Public Subnets (Web Tier):
│ ├── 10.0.1.0/24 (us-east-1a) - Accepts internet traffic
│ └── 10.0.2.0/24 (us-east-1b) - Accepts internet traffic
├── Private Subnets (App Tier):
│ ├── 10.0.3.0/24 (us-east-1a) - No internet access
│ └── 10.0.4.0/24 (us-east-1b) - No internet access
└── Isolated Subnets (DB Tier):
├── 10.0.5.0/24 (us-east-1a) - Most restricted
└── 10.0.6.0/24 (us-east-1b) - Most restricted


## 📊 Understanding Connections Through Diagrams

### Public Subnet vs Private Subnet

**Public Subnet Meaning:**
A subnet that has a route to an Internet Gateway, allowing resources within it to communicate directly with the internet.

**Key Characteristics:**
- Has a route table entry: 0.0.0.0/0 → igw-xxxxx
- Resources can have public IP addresses
- Direct inbound/outbound internet access
- Typically used for load balancers, web servers, NAT gateways

**Private Subnet Meaning:**
A subnet that does NOT have a direct route to the internet. Resources in private subnets cannot be accessed directly from the internet.

**Key Characteristics:**
- No direct route to Internet Gateway
- Resources typically have only private IP addresses
- Can access internet through NAT Gateway (outbound only)
- Typically used for application servers, databases, internal services

### Network Architecture Diagram
🌐 INTERNET
│
↓
🔗 Internet Gateway (igw-xxxxx)
│
↓
🏢 VPC: 10.0.0.0/16
│
├── 🟢 PUBLIC SUBNET (10.0.1.0/24 - us-east-1a)
│ │
│ ├── 🖥️ Web Server EC2
│ │ ├── Public IP: 203.0.113.10
│ │ ├── Private IP: 10.0.1.20
│ │ └️ Security Group: Allow HTTP/HTTPS from internet
│ │
│ ├── ⚖️ Application Load Balancer
│ │ ├── DNS: my-app-123456.us-east-1.elb.amazonaws.com
│ │ └️ Security Group: Allow HTTP/HTTPS from internet
│ │
│ └── 🌐 NAT Gateway
│ ├── Public IP: 203.0.113.20
│ └️ Route: Provides internet access for private subnets
│
├── 🔒 PRIVATE SUBNET (10.0.2.0/24 - us-east-1b)
│ │
│ ├── 🖥️ Application Server EC2
│ │ ├── Private IP: 10.0.2.30
│ │ ├── No public IP
│ │ └️ Security Group: Allow from Web Server SG only
│ │
│ ├── 🗃️ Database Server (Amazon RDS)
│ │ ├── Private IP: 10.0.2.40
│ │ └️ Security Group: Allow from App Server SG only
│ │
│ └️ Route Table: 0.0.0.0/0 → nat-gateway (not internet gateway)
│
└── 🔐 ISOLATED SUBNET (10.0.3.0/24 - us-east-1c)
│
└── 💾 Backup Database
├── Private IP: 10.0.3.50
└️ No internet access at all

🔄 TRAFFIC FLOW:
Internet User → Internet Gateway → Public Subnet (ALB) →
Private Subnet (App Server) → Private Subnet (Database)

### How Public and Private Subnets Work Together

**Public Subnet Traffic Flow:**

🌐 Internet User (requests website)
↓
🔗 Internet Gateway (routes to public subnet)
↓
🏢 Public Subnet - ALB (receives request)
↓
🔒 Private Subnet - App Server (processes request)
↓
🔒 Private Subnet - Database (fetches data)
↓
🔄 Response travels back through same path

**Private Subnet Internet Access:**

🔒 Private Subnet - App Server (needs to download updates)
↓
🌐 NAT Gateway in Public Subnet (translates private to public IP)
↓
🔗 Internet Gateway (connects to internet)
↓
🌐 External Update Server
↓
🔄 Response comes back through NAT Gateway


## 🎯 Key Differences: Public vs Private Subnets

| Characteristic | Public Subnet | Private Subnet |
|---------------|---------------|----------------|
| **Internet Access** | Direct (via IGW) | Indirect (via NAT) |
| **Public IPs** | Can have public IPs | Typically private IPs only |
| **Security** | Exposed to internet | Protected from direct internet access |
| **Use Cases** | Web servers, load balancers | App servers, databases |
| **Cost** | Data transfer costs | + NAT Gateway costs |
| **Route Table** | 0.0.0.0/0 → igw | 0.0.0.0/0 → nat-gateway |

## 💡 Real-World Scenario: Online Bank Application

**Public Subnet Components:**
- **Web Application Load Balancer:** Handles customer login requests
- **Bastion Host:** Secure admin access point
- **NAT Gateway:** Provides internet access for private resources

**Private Subnet Components:**
- **Application Servers:** Process banking transactions
- **Customer Database:** Stores account information
- **Transaction Database:** Records all financial transactions

**Security Benefits:**
- 🛡️ Customer data never exposed to public internet
- 🔒 Database servers completely isolated
- ⚡ Web servers can scale without security concerns
- 🔐 Administrative access controlled through bastion host

## 🚀 Best Practices for Subnet Design

1. **Use Multiple AZs:** Distribute subnets across Availability Zones
2. **Plan IP Ranges:** Leave room for future expansion
3. **Tier Your Architecture:** Web → App → Database subnets
4. **Implement Security Layers:** Security Groups + NACLs
5. **Monitor Traffic:** Use VPC Flow Logs for visibility
6. **Document Your Design:** Keep network diagrams updated

This foundation in VPC and subnet design is crucial for building secure, scalable, and highly available applications on AWS.









✅ Completed on: [Insert Date]
