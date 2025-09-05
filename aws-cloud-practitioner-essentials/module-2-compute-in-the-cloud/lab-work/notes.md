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

## 💰 AWS Pricing Options & Cost Optimization

### 🏷️ EC2 Pricing Models

#### 1. On-Demand Instances
**Meaning:** Pay for compute capacity by the second or hour with no long-term commitments.
**Best For:** Short-term, unpredictable workloads that cannot be interrupted
**Example:** Development and test environments, applications with unpredictable traffic patterns

#### 2. Reserved Instances (RIs)
**Meaning:** Significant discount (up to 75%) compared to On-Demand pricing in exchange for a 1 or 3-year commitment
**Types:**
- **Standard RIs:** Largest discount, capacity reservation
- **Convertible RIs:** Can exchange for different instance types, lower discount
- **Scheduled RIs:** Launch within specified time windows
**Example:** Production databases, steady-state applications

#### 3. Savings Plans
**Meaning:** Flexible pricing model offering lower prices in exchange for a commitment to consistent usage ($/hour) for 1 or 3 years
**Types:**
- **Compute Savings Plans:** Most flexible, applies across EC2, Fargate, Lambda
- **EC2 Instance Savings Plans:** Specific to EC2 instance families in a region
**Example:** Commit to $10/hour for 1 year, get discounted rates on any usage above that commitment

#### 4. Spot Instances
**Meaning:** Purchase unused EC2 capacity at up to 90% discount, but can be terminated with 2-minute notice
**Best For:** Fault-tolerant, flexible applications that can handle interruptions
**Example:** Big data processing, containerized workloads, CI/CD pipelines

#### 5. Dedicated Instances
**Meaning:** Instances running on hardware dedicated to a single AWS customer, no other customers share the hardware
**Features:**
- Hardware isolation at the host level
- May share hardware with other instances from same AWS account
- No control over instance placement
**Example:** Regulatory requirements requiring hardware isolation

#### 6. Dedicated Hosts
**Meaning:** Physical server fully dedicated for your use, providing additional visibility and control over how instances are placed
**Features:**
- Complete control over instance placement
- Bring-your-own-license (BYOL) benefits
- Per-socket or per-core pricing available
- Most expensive dedicated option
**Example:** Applications requiring specific socket/core counts for licensing compliance

### ⚖️ Dedicated Hosts vs. Dedicated Instances
| Feature | Dedicated Hosts | Dedicated Instances |
|---------|-----------------|---------------------|
| **Hardware Control** | Full control over instance placement | No control over placement |
| **Visibility** | See sockets, cores, host ID | No host-level visibility |
| **Licensing** | BYOL benefits available | Standard AWS licensing |
| **Cost** | Higher cost | Lower cost than Dedicated Hosts |
| **Use Case** | License compliance, regulatory requirements | General hardware isolation needs |

### 🎯 Cost Optimization Strategies

#### 1. Savings Plans
**Meaning:** Commit to consistent usage amount ($/hour) for 1 or 3 years for significant discounts
**Flexibility:** Can be applied across instance families, sizes, regions, and even services
**Example:** Commit to $20/hour for 3 years, get up to 72% discount on all usage above commitment

#### 2. Capacity Reservations
**Meaning:** Reserve capacity in a specific Availability Zone for any duration, paying On-Demand rates regardless of usage
**Benefits:** 
- Ensure capacity when needed
- Combine with Savings Plans for cost savings
- No long-term commitment required
**Example:** Reserve capacity for holiday season traffic spikes

#### 3. Reserved Instance Flexibility
**Meaning:** Options to modify existing RIs to accommodate changing needs
**Features:**
- **Size Flexibility:** Exchange RIs for different sizes in same instance family
- **Regional Benefits:** Some RIs can be applied across Availability Zones in a region
- **Convertible Option:** Exchange RIs for different instance types with convertible RIs
**Example:** Exchange 4 large instances for 8 medium instances as workload changes

### 💡 Cost Optimization Best Practices
1. **Right-Sizing:** Regularly review and adjust instance types to match workload requirements
2. **Instance Scheduling:** Automate start/stop for non-production instances
3. **Spot Integration:** Use Spot Instances for appropriate workloads
4. **Commitment Management:** Use Savings Plans for baseline usage, On-Demand for variable usage
5. **Regular Review:** Use Cost Explorer and AWS Budgets to monitor and optimize spending

## 📈 Scaling Amazon EC2: Scalability and Elasticity

### ⚖️ Scalability vs. Elasticity

#### Scalability
**Meaning:** The ability to increase or decrease compute resources to handle changing workload demands, typically through manual intervention or planned scaling.

**Characteristics:**
- Planned capacity changes
- Manual or scheduled adjustments
- Handles predictable workload changes
- Maintains capacity until manually adjusted

**Example:** 
- An e-commerce website adding more servers before Black Friday sales
- A university adding capacity before online course registration opens
- A business expanding server capacity to support company growth

#### Elasticity
**Meaning:** The ability to automatically increase or decrease compute resources in response to changing workload demands in real-time.

**Characteristics:**
- Automatic scaling based on metrics
- Responds to unpredictable traffic patterns
- Scales down during low usage to save costs
- Managed by AWS Auto Scaling services

**Example:**
- A news website automatically adding servers during breaking news events
- A streaming service scaling up during prime time and down overnight
- An application handling sudden viral traffic spikes

### 🔄 Amazon EC2 Auto Scaling Components

#### 1. Minimum Capacity
**Meaning:** The minimum number of instances that must be running in your Auto Scaling group at all times, regardless of demand.

**Purpose:**
- Ensures baseline performance
- Maintains availability for steady-state traffic
- Handles minimum expected workload

**Example:** 
- Setting minimum capacity to 2 instances for a web application
- Ensuring at least 1 instance is always available for critical applications
- Maintaining baseline processing capacity for ongoing operations

#### 2. Desired Capacity
**Meaning:** The number of instances that the Auto Scaling group attempts to maintain, which can be manually adjusted or automatically managed by scaling policies.

**Purpose:**
- Represents the ideal number of instances for current conditions
- Auto Scaling works to maintain this number
- Can be manually set or automatically adjusted

**Example:**
- Setting desired capacity to 4 instances during business hours
- Automatically adjusting between 2-8 instances based on CPU utilization
- Maintaining optimal performance for current traffic levels

#### 3. Maximum Capacity
**Meaning:** The maximum number of instances that the Auto Scaling group can scale out to, providing an upper bound for automatic scaling.

**Purpose:**
- Preoverscaling and excessive costs
- Ensures resources stay within budget constraints
- Provides safety limit for automatic scaling

**Example:**
- Setting maximum capacity to 10 instances to control costs
- Limiting scaling to avoid exceeding budget during traffic spikes
- Ensuring resources stay within architectural limits

### 🎯 Auto Scaling Configuration Example

Auto Scaling Group Configuration:
- Minimum capacity: 2 instances
- Desired capacity: 4 instances  
- Maximum capacity: 10 instances
- Scaling policy: Scale out when CPU > 70%, scale in when CPU < 30%

## 🌐 Elastic Load Balancing (ELB)

### 📖 What is Elastic Load Balancing?
**Meaning:** A AWS service that automatically distributes incoming application traffic across multiple targets (such as EC2 instances, containers, IP addresses) in one or more Availability Zones.

**Key Purpose:** 
- Improves application availability and fault tolerance
- Distributes traffic evenly to prevent any single resource from being overwhelmed
- Provides seamless scalability for applications

**Example:** 
- An e-commerce website distributing user requests across 10 EC2 instances
- A mobile game backend spreading player connections across multiple servers
- An API service balancing requests across different availability zones

### 🎯 ELB Benefits

#### 1. Efficient Traffic Distribution
**Meaning:** Automatically routes incoming traffic to healthy targets while avoiding overloaded or unhealthy instances.

**How it works:**
- Continuously monitors target health
- Only sends traffic to targets that can handle requests
- Distributes load based on configured routing algorithm

**Example:**
- During peak shopping hours, ELB directs users to available servers instead of overloaded ones
- If one server has high CPU usage, ELB routes new requests to less busy servers

#### 2. Automatic Scaling
**Meaning:** Works seamlessly with Auto Scaling to automatically adjust to changing traffic patterns without manual intervention.

**How it works:**
- Integrates with Amazon EC2 Auto Scaling
- Automatically registers new instances as they come online
- Deregisters instances that are terminated or unhealthy

**Example:**
- During flash sale, Auto Scaling adds 20 new instances and ELB immediately starts sending traffic to them
- After traffic decreases, ELB stops sending requests to instances being terminated

#### 3. Simplified Management
**Meaning:** Provides a single point of contact for clients while handling complex routing decisions behind the scenes.

**How it works:**
- Single DNS name for applications
- Automatic certificate management with AWS Certificate Manager
- Built-in security features and logging

**Example:**
- Developers only need to point their domain to the load balancer DNS
- SSL/TLS certificates automatically renewed and deployed
- Centralized access logs for all application traffic

### 🔄 Routing Methods (Load Balancing Algorithms)

#### 1. Round Robin
**Meaning:** Distributes requests sequentially to each target in rotation, regardless of current load.

**Best for:** Applications where all targets have similar capacity
**Example:** Distributing API requests equally across 5 identical EC2 instances

#### 2. Least Connections
**Meaning:** Routes traffic to the target with the fewest active connections.

**Best for:** Applications with varying request processing times
**Example:** Video streaming service where some users watch HD content (long connections) and others browse (short connections)

#### 3. IP Hash
**Meaning:** Uses the client's IP address to determine which target receives the request, ensuring same client goes to same target.

**Best for:** Applications requiring session persistence
**Example:** Shopping cart application where user session data is stored on specific servers

#### 4. Least Response Time
**Meaning:** Routes traffic to the target with the fastest response time and fewest active connections.

**Best for:** Applications requiring optimal performance
**Example:** Real-time gaming platform where low latency is critical

### 📈 ELB in Action: Traffic Flow Examples

#### Initial Setup (Low-Demand Period)
**Scenario:** Application running with minimal traffic
**Configuration:**
- 2 EC2 instances running
- ELB health checks monitoring both instances
- Round Robin routing configured

**Example:** 
- 100 users accessing a blog website
- ELB sends 50 requests to Instance A, 50 to Instance B
- Both instances operating at 30% CPU utilization

#### Scaling Up (High-Demand Period)
**Scenario:** Sudden traffic spike occurs
**Configuration:**
- Auto Scaling group configured to scale at 70% CPU
- ELB automatically registers new instances

**Example:**
- News website during breaking news event
- Traffic increases from 100 to 10,000 users
- Auto Scaling adds 8 more instances (total 10)
- ELB immediately starts distributing traffic to all 10 instances
- Each instance handles ~1,000 users instead of 5,000

#### Load Balancing (Traffic Distribution)
**Scenario:** Ongoing traffic management
**Configuration:**
- Least Connections routing enabled
- Health checks configured every 30 seconds

**Example:**
- E-commerce site during holiday sale
- Some users browsing (short sessions), others checking out (long sessions)
- ELB detects Instance C has many long checkout sessions
- New browsing requests routed to Instance A and B with shorter sessions
- Prevents checkout process from being slowed down by browse traffic

### 🛡️ ELB Types and Use Cases

**Application Load Balancer (ALB):**
- Layer 7 load balancing
- Best for HTTP/HTTPS traffic
- Advanced routing based on content

**Network Load Balancer (NLB):**
- Layer 4 load balancing  
- Best for extreme performance
- TCP/UDP traffic handling

**Gateway Load Balancer (GWLB):**
- For third-party virtual appliances
- Security and compliance workloads

**Classic Load Balancer (CLB):**
- Legacy load balancer
- Basic Layer 4/Layer 7 features

## 📨 Messaging and Queuing in AWS

### 🔄 Decoupling Services

#### Monolithic Applications
**Meaning:** A single, unified application where all components are tightly interconnected and run as a single service.

**Characteristics:**
- All components share the same memory space and resources
- Single codebase and deployment unit
- Components communicate through function calls
- Failure in one component can affect entire application

**Example:**
- Traditional e-commerce app where product catalog, shopping cart, and payment processing are all in one application
- If the payment service fails, the entire application becomes unavailable
- Scaling requires scaling the entire application, even if only one component needs more resources

#### Microservices Architecture
**Meaning:** An architectural style where applications are composed of small, independent services that communicate over well-defined APIs.

**Characteristics:**
- Each service runs its own process and can be deployed independently
- Services communicate through lightweight mechanisms (HTTP, messaging)
- Failure isolation - one service can fail without affecting others
- Each service can be scaled independently based on demand

**Example:**
- Modern e-commerce app with separate services for:
  - Product catalog service
  - Shopping cart service  
  - Payment processing service
  - User authentication service
- If payment service fails, users can still browse products and add items to cart
- Each service can be scaled independently based on specific needs

### 🌉 Supporting Scalable and Reliable Cloud Communication

#### Amazon EventBridge
**Meaning:** A serverless event bus service that makes it easy to connect applications using data from your own applications, integrated Software-as-a-Service (SaaS) applications, and AWS services.

**How EventBridge Helps in AWS:**
- **Event-Driven Architecture:** Enables reactive applications that respond to events in real-time
- **Decoupling:** Services don't need to know about each other, only about the events
- **Scalability:** Automatically scales with your event volume
- **Integration:** Connects AWS services, your applications, and third-party SaaS applications

**Examples:**

1. **Payment Processing:**
   - Event: `payment.processed`
   - Actions: Update order status + send confirmation email + update inventory
   - Services: Lambda functions triggered by payment events

2. **Restaurant Notification:**
   - Event: `order.placed`  
   - Actions: Notify kitchen + update display + send SMS to customer
   - Services: SNS topics + Lambda functions

3. **Inventory Management:**
   - Event: `inventory.low`
   - Actions: Generate purchase order + notify manager + update dashboard
   - Services: SQS queue + Lambda + SNS

4. **Delivery Dispatch:**
   - Event: `order.ready.for.delivery`
   - Actions: Assign driver + update tracking + notify customer
   - Services: Step Functions + Lambda + SNS

### 📦 Amazon Simple Queue Service (SQS)

**Meaning:** A fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications.

**Key Features:**
- **Message Persistence:** Messages are stored until processed
- **At-Least-Once Delivery:** Messages are delivered at least once
- **Visibility Timeout:** Prevents other consumers from processing the same message
- **Dead Letter Queues:** Handles messages that can't be processed successfully

**Examples:**
- **Order Processing Queue:** Orders are placed in queue and processed by multiple worker services
- **Image Processing:** Thumbnail generation requests queued for asynchronous processing
- **Email Notification Queue:** Batch processing of email notifications without affecting main application

### 📢 Amazon Simple Notification Service (SNS)

**Meaning:** A fully managed pub/sub messaging service that enables message delivery to a large number of subscribers.

**Key Features:**
- **Pub/Sub Model:** Publishers send messages to topics, subscribers receive them
- **Multiple Protocols:** Supports HTTP, HTTPS, Email, SMS, Lambda, SQS
- **Fanout Pattern:** Single message to multiple subscribers
- **Serverless:** Automatically scales with message volume

#### SNS Use Cases:

**1. Segment the Communication:**
- **Meaning:** Create different topics for different types of messages
- **Example:** 
  - `order.updates` topic for order status changes
  - `system.alerts` topic for critical system notifications
  - `marketing.emails` topic for promotional content

**2. Let Customers Choose Topics:**
- **Meaning:** Allow subscribers to choose which notifications they want to receive
- **Example:**
  - Customers can subscribe to: "Order Updates", "Promotional Offers", "Security Alerts"
  - Each subscription type goes to different SNS topics
  - Users receive only what they've opted into

**3. Send Tailored Notifications:**
- **Meaning:** Customize messages based on subscriber preferences or characteristics
- **Example:**
  - Different message formats for email vs. SMS subscribers
  - Regional promotions based on subscriber location
  - Personalized content based on user preferences

### 🏗️ Architecture Comparison

SQS vs. SNS vs. EventBridge:

SQS: Point-to-point messaging (1:1)

Producer → Queue → Consumer

Best for: Task distribution, workload processing

SNS: Pub/Sub messaging (1:many)

Producer → Topic → Multiple Subscribers

Best for: Fanout, notifications, alerts

EventBridge: Event-driven architecture

Event Source → Event Bus → Multiple Targets

Best for: Application integration, workflow automation

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
