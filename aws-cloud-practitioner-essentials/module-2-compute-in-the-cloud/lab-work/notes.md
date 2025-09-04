# Module 2: Compute in the Cloud

## 🌐 What is Cloud Compute?
Compute refers to the processing power required to run applications, manage data, and perform calculations.

## 🏗️ Amazon EC2 Instance Types

| Instance Type | Purpose | Ideal Workloads |
|---------------|---------|-----------------|
| **General Purpose** | Balanced compute, memory, and networking | Web servers, small databases, development environments 
| **Compute Optimized** | High-performance processors | Batch processing, scientific modeling, gaming servers 
| **Memory Optimized** | Process large datasets in memory | In-memory databases, big data processing 
| **Storage Optimized** | High, sequential read/write access to large datasets | Data warehousing, distributed file systems 
| **Accelerated Computing** | Hardware accelerators (e.g., GPUs) | Graphics processing, machine learning 

## 📸 Amazon Machine Images (AMI)

An AMI is a template containing the software configuration (OS, applications, settings) required to launch an EC2 instance.

### 🧩 AMI Components:
- **Root Volume Template**: OS, applications, and configurations
- **Launch Permissions**: Controls which accounts can use the AMI (public/private/shared)
- **Block Device Mapping**: Specifies storage volumes to attach
- **Instance Type Support**: Determines compatible EC2 instance types

### 🚀 Three Ways to Use AMIs:

#### 1. Create Your Own Custom AMI
**Meaning:** Build customized images from configured EC2 instances with your specific software and settings.

**Example:** Creating an AMI with Apache, PHP, MySQL, and your web application pre-installed.

#### 2. Use Available AWS AMIs  
**Meaning:** Use pre-configured images provided and maintained by AWS.

**Types:**
- Amazon Linux & Amazon Linux 2 (AWS-optimized)
- Windows Server versions
- Ubuntu, Red Hat, SUSE Linux distributions

**Benefits:**
- Free to use (only pay for EC2 resources)
- Regularly security-patched by AWS
- Optimized for AWS environment

#### 3. Purchase from AWS Marketplace
**Meaning:** Use specialized AMIs created by third-party vendors with commercial software.

**Use Cases:**
- Commercial software (MATLAB, Oracle, SAP)
- Pre-configured solutions (WordPress, security appliances)
- Industry-specific applications

**Pricing Models:**
- Free (only EC2 costs)
- Hourly usage fees
- Annual subscription fees

### 🔄 AMI Repeatability
**Meaning:** The ability to consistently recreate identical environments from the same AMI.

**Benefits:**
- Environment consistency across development/staging/production
- Rapid scaling of identical instances
- Disaster recovery and quick environment recreation
- Version control for infrastructure

**Best Practices:**
- Use Golden AMI approach for production
- Automate AMI building with tools like Packer
- Implement versioning and change logs
- Thoroughly test new AMIs before production use

## 🖥️ Methods to Interact with AWS Services

AWS provides three main ways to interact with their services:

| Method | Description | Best For |
|--------|-------------|----------|
| **AWS Management Console** | Web-based graphical interface for point-and-click management | Beginners, manual operations, visual learners |
| **AWS Command Line Interface (CLI)** | Command-line tool for scripting and automation | Developers, automated tasks, repetitive operations |
| **AWS Software Development Kits (SDKs)** | Language-specific libraries for integrating AWS into applications | Application development, custom solutions, programmers |

### Key Differences:
- **Console**: Visual, no coding required
- **CLI**: Scriptable, command-based
- **SDKs**: Programmatic, integrated into application code

## ☁️ AWS Compute Services

**Compute** refers to the on-demand processing capacity that runs applications in the AWS cloud. Instead of physical servers, AWS provides virtualized, scalable resources.

**Main AWS Compute Services:**
- **EC2 (Elastic Compute Cloud)**: Virtual servers with full control
- **Lambda**: Serverless functions that run code without provisioning servers
- **ECS/EKS**: Container management services
- **Fargate**: Serverless compute for containers
- **Elastic Beanstalk**: Automated deployment and scaling of web apps

## 🔐 AWS Shared Responsibility Model

The Shared Responsibility Model defines security responsibilities between AWS and customers:

**AWS is responsible for security OF the cloud:**
- Global infrastructure security
- Hardware and software maintenance
- Host operating system and virtualization
- Physical data center security

**Customer is responsible for security IN the cloud:**
- Guest operating system management
- Application security and data encryption
- Security group and firewall configurations
- IAM user access and permissions
- Network traffic protection

## 🤝 Multi-Tenancy in Cloud Computing
Multi-tenancy is a fundamental cloud architecture where multiple customers (tenants) share the same physical infrastructure while maintaining logical isolation of their data and applications.

## 💡 Key Concepts
- **Scalability**: The ability to easily increase or decrease compute resources based on demand.
- **Elasticity**: The ability to acquire resources as you need them and release them when you don't.

## 🛠️ Hands-On Practice
- Launched a `t2.micro` EC2 instance (Free Tier eligible).
- Explored the EC2 dashboard and instance details.

---
✅ Completed on: 
