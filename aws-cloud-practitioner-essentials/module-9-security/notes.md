# Introduction to Security on AWS

## Authentication and Authorization

### Authentication

#### Definition:
- **Process of verifying identity** of a user or entity
- **Credentials required**: Username, password, biometrics, MFA tokens
- **Answers the question**: "Who are you?"

#### Use Case Example:
- **Employee logs in** to an employee portal using username and password
- System verifies the credentials match a valid user
- If credentials are correct, authentication succeeds

#### Key Points:
- **First step** in access control
- Establishes identity
- Can use single-factor (password) or multi-factor (password + MFA)
- Does NOT determine what you can do

### Authorization

#### Definition:
- **Grants access rights and permissions** to authenticated users
- **Determines actions** a user can perform in a system
- **Answers the question**: "What are you allowed to do?"

#### Use Case Example:
- After logging in, employee can **only access their own records**
- Cannot view other employees' information
- Permissions are limited to necessary functions

#### Key Points:
- **Second step** after authentication
- Defines allowed actions (read, write, delete, etc.)
- Enforces the principle of least privilege
- Scope can be specific (one record) or broad (entire system)

### Authentication vs Authorization Comparison

| Aspect | Authentication | Authorization |
|--------|---------------|---------------|
| **Purpose** | Verify identity | Grant permissions |
| **Question** | Who are you? | What can you do? |
| **Order** | First | Second |
| **Example** | Login with password | Access only your records |
| **Analogies** | Showing ID at airport | Boarding pass allows on plane |
| **AWS Service** | IAM user login, MFA | IAM policies |

### Visual Example:

User enters username/password → AUTHENTICATION (Identity verified)
↓
User requests access to records → AUTHORIZATION (Permission checked)
↓
User can only access own records → ACCESS GRANTED


## AWS Shared Responsibility Model

### Overview:
- **Cloud security is shared** between AWS and customers
- **Clear division**: AWS secures the cloud, customers secure in the cloud
- **No single party** is responsible for everything
- **Understanding this model** is critical for exam and real-world security

### Customer Responsibility: Security IN the Cloud

#### What Customers Control:
- **Customer maintains complete control** over their content
- **Responsible for everything** they create and manage in AWS

#### Customer Responsibilities Include:

##### 1. Data and Content Security
- **Managing security of data**, systems, and applications
- **Data classification** and encryption
- **Access controls** for their resources
- **Backup and recovery** planning

##### 2. Workload Decisions
- **Deciding what data and workloads** to store or run in AWS
- **Choosing appropriate AWS services** for specific needs
- **Determining deployment architectures**

##### 3. Service Configuration
- **Determining which AWS services** to use
- **Configuring services securely** according to best practices
- **Managing service-specific security settings**

##### 4. Access Management
- **Controlling who has access** to environments and resources
- **Managing user identities** and permissions
- **Implementing least privilege access**

##### 5. Application Security
- **Securing applications** deployed on AWS
- **Writing secure code** and managing dependencies
- **Application-level authentication and authorization**

### AWS Responsibility: Security OF the Cloud

#### What AWS Controls:
- **AWS operates, manages, and controls** components at all infrastructure layers
- **Responsible for the foundation** that services run on

#### AWS Responsibilities Include:

##### 1. Foundational Software
- **Software that powers AWS services**
- **Hypervisor layer** that separates customer instances
- **Operating systems** on AWS-managed infrastructure

##### 2. Virtualization Layer
- **Hardware virtualization** that enables multi-tenancy
- **Isolation between customer resources**
- **Hypervisor security** and updates

##### 3. Hardware Infrastructure
- **Servers**, storage devices, and networking equipment
- **Physical security** of data centers
- **Power, cooling, and environmental controls**

##### 4. Global Infrastructure
- **AWS Regions** - geographic locations
- **Availability Zones** - isolated data center clusters
- **Edge Locations** - content delivery endpoints
- **Physical network** connecting all components

##### 5. Managed Service Components
- **For managed services** (RDS, DynamoDB, etc.), AWS handles more
- **Database engine patching** for managed services
- **Infrastructure maintenance** for all services

### Shared Responsibility Model Visualization:

─────────────────────────────────────────────────┐
│ CUSTOMER (IN the cloud) │
│ • Data & Content Security │
│ • Applications & Configuration │
│ • Access Management │
│ • Service Selection & Usage │
├─────────────────────────────────────────────────┤
│ AWS (OF the cloud) │
│ • Hardware & Global Infrastructure │
│ • Virtualization Layer │
│ • Foundational Software │
│ • Physical Security │
└───────────────────────────

### Service Category Variations:

#### Infrastructure Services (EC2, EBS, VPC):
- **Customer manages more**: OS, applications, network configuration
- **AWS manages**: Physical hardware, virtualization

#### Container Services (ECS, EKS):
- **Shared responsibility**: AWS manages orchestration, customer manages containers
- **Customer manages**: Container images, application code

#### Abstracted Services (S3, DynamoDB, Lambda):
- **AWS manages more**: Serverless, no customer access to underlying OS
- **Customer manages**: Data, configuration, access policies

### Shared Responsibility Examples:

| Responsibility Area | Customer | AWS |
|--------------------|----------|-----|
| **Physical Security** | No | Yes |
| **Hypervisor Security** | No | Yes |
| **Network Infrastructure** | No | Yes |
| **OS Patching (EC2)** | Yes | No |
| **Database Configuration** | Yes (on EC2) / No (on RDS) | No (on EC2) / Yes (on RDS) |
| **Data Encryption** | Yes | Provides tools |
| **IAM Configuration** | Yes | No |
| **Application Code** | Yes | No |

## AWS Security Controls

### Purpose of Security Controls:
- **Prevent security incidents** before they happen
- **Protect networks, applications, and data**
- **Detect and respond** to incidents as they occur
- **Provide defense in depth** across multiple layers

### Three Categories of Security Controls:

#### 1. Preventive Controls

##### Purpose:
- **Stop security incidents** from occurring
- **Block unauthorized access** before it happens
- **Enforce security policies** proactively

##### Examples from AWS:
- **IAM**: Proper permission and access management
- **Security Groups**: Instance-level firewalls
- **Network ACLs**: Subnet-level access control
- **AWS WAF**: Block malicious web traffic
- **Encryption**: Protect data at rest and in transit

##### Key Quote from Notes:
> "Prevent security incidents through proper permission and access management."

#### 2. Detective Controls

##### Purpose:
- **Identify security incidents** as they occur
- **Monitor for suspicious activity**
- **Provide visibility** into security posture

##### Examples from AWS:
- **Amazon GuardDuty**: Threat detection
- **AWS CloudTrail**: API activity logging
- **Amazon Inspector**: Vulnerability assessment
- **AWS Config**: Configuration monitoring
- **Amazon Macie**: Sensitive data discovery

##### Key Quote from Notes:
> "Detect and respond to security incidents as they occur."

#### 3. Protective Controls

##### Purpose:
- **Limit impact** of security incidents
- **Safeguard resources** during an attack
- **Maintain availability** under duress

##### Examples from AWS:
- **AWS Shield**: DDoS protection
- **AWS WAF**: Web application firewall
- **Auto Scaling**: Maintain capacity during attacks
- **Backup and Recovery**: Restore after incidents

##### Key Quote from Notes:
> "Protect networks, applications, and data."

### Defense in Depth Strategy:

Layer 1: Preventive Controls (IAM, Security Groups)
↓
Layer 2: Protective Controls (Shield, WAF)
↓
Layer 3: Detective Controls (GuardDuty, CloudTrail)
↓
Layer 4: Response (Automated + Manual)


## Exam Critical Points

### Must Remember Definitions:

#### Authentication:
- **Verifying identity** (username/password, MFA)
- "Who are you?"
- First step in access control

#### Authorization:
- **Granting permissions** (what you can do)
- "What are you allowed to do?"
- Second step after authentication

### Shared Responsibility Model:

#### Customer: Security IN the Cloud
- **Data, applications, access management**
- **Service configuration**
- **What you put IN AWS**

#### AWS: Security OF the Cloud
- **Hardware, software, networking**
- **Global infrastructure**
- **What AWS provides**

### Three Control Categories:

| Category | Purpose | Examples |
|----------|---------|----------|
| **Preventive** | Stop incidents | IAM, Security Groups, WAF |
| **Detective** | Identify incidents | GuardDuty, CloudTrail, Inspector |
| **Protective** | Limit impact | Shield, backups, auto scaling |

### Common Exam Scenarios:

#### Authentication vs Authorization:
- **Login process** = Authentication
- **Access to specific resources** = Authorization
- **MFA** = Authentication enhancement
- **IAM policies** = Authorization tool

#### Shared Responsibility:
- **EC2 instance OS patching** = Customer responsibility
- **Physical data center security** = AWS responsibility
- **RDS database encryption** = Customer configures, AWS provides tools
- **S3 bucket permissions** = Customer responsibility

### Key Takeaways:
1. **Authentication proves who you are**, authorization determines what you can do
2. **AWS secures the infrastructure**, customers secure their content and configuration
3. **Multiple control types** work together for comprehensive security
4. **Defense in depth** uses layers of preventive, detective, and protective controls
5. **Understand your responsibilities** based on which services you use

# Protecting Networks and Applications

## Network and Application Attacks

### Overview
- **Critical Security Component**: Protecting networks and applications from attacks
- **Common Threat**: Denial of Service (DoS) and Distributed Denial of Service (DDoS)
- **AWS Approach**: Built-in infrastructure protection + specialized security services

## Denial of Service (DoS) Attacks

### What is a DoS Attack?
- **Definition**: An attacker floods a web application with excessive network traffic
- **Goal**: Overwhelm the application so it can no longer respond to legitimate users
- **Result**: Legitimate customer requests are denied service

### How DoS Attacks Work:
Attacker → Excessive Traffic → Web Application → Overloaded → Denies Legitimate Users

### Characteristics:
- **Single Source**: Attack comes from one computer or IP address
- **Resource Exhaustion**: Consumes server resources (CPU, memory, bandwidth)
- **Application Crash**: Server becomes unresponsive or crashes
- **Business Impact**: Lost revenue, customer dissatisfaction, brand damage

### Common DoS Attack Types:

#### Volume-Based Attacks:
- **UDP Floods**: Overwhelm with User Datagram Protocol packets
- **ICMP Floods**: Ping of death using ICMP echo requests
- **Bandwidth Saturation**: Consume all available network bandwidth

#### Protocol Attacks:
- **SYN Flood**: Exploit TCP handshake process
- **Fragmentation Attacks**: Send malformed packet fragments
- **Connection Exhaustion**: Use up all available connections

#### Application Layer Attacks:
- **HTTP Floods**: Overwhelm web servers with HTTP requests
- **Slowloris**: Slow connections that hold resources open
- **API Abuse**: Target specific API endpoints

## Distributed Denial of Service (DDoS) Attacks

### What is a DDoS Attack?
- **Definition**: Multiple infected computers send excessive traffic to a target
- **Distributed Nature**: Attack comes from many sources simultaneously
- **Scale**: Much larger volume than single-source DoS attacks

### How DDoS Attacks Work:

#### Zombie Bots:
- **Infected Computers**: Attacker compromises many computers (bots)
- **Botnet**: Network of infected computers under attacker's control
- **Unknowing Participants**: Computer owners don't know their devices are being used
- **Command & Control**: Attacker sends instructions to all bots simultaneously

Attacker → Command & Control → Botnet (thousands of infected computers)
↓
Target Web Application
(Overwhelmed by traffic from all bots)


### DDoS Attack Characteristics:

#### Scale:
- **Massive Traffic**: Can generate terabytes of traffic per second
- **Global Distribution**: Bots located around the world
- **Difficult to Block**: Many different IP addresses to filter
- **Amplification**: Some attacks multiply traffic volume

#### Complexity:
- **Multi-Vector**: Often combine different attack types
- **Evolving Techniques**: Attackers constantly develop new methods
- **Application Targeting**: Sophisticated attacks target application logic
- **Hard to Distinguish**: Malicious traffic may look like legitimate traffic

### DDoS Attack Examples:

#### IoT Botnets:
- **Compromised Devices**: Cameras, routers, smart devices
- **Mirai Botnet**: Famous example that took down major websites
- **Massive Scale**: Hundreds of thousands of devices

#### Reflection Attacks:
- **DNS Amplification**: Small queries generate large responses
- **NTP Amplification**: Exploit Network Time Protocol servers
- **Spoofed Source**: Make responses go to target

## AWS Network and Application Protection

### AWS Infrastructure Protection

#### Built-in Capabilities:
- **Automatic Protection**: AWS automatically protects against low-level, brute-force attacks
- **Infrastructure Design**: Global architecture makes overwhelming the system difficult
- **No Additional Cost**: Basic DDoS protection included with all AWS services

#### Global Infrastructure Advantages:

##### Multiple Regions:
- **Geographic Distribution**: AWS operates in multiple Regions worldwide
- **Traffic Distribution**: Load can be spread across Regions
- **Regional Isolation**: Attack on one Region doesn't affect others
- **Geographic Diversity**: Makes attacks harder to coordinate

##### Availability Zones:
- **Physical Separation**: Each Region has multiple isolated AZs
- **Redundancy**: Applications can run across multiple AZs
- **Fault Tolerance**: Attack on one AZ doesn't take down entire application
- **Automatic Failover**: Traffic can shift to healthy AZs

##### Edge Locations:
- **Global Network**: Over 400+ edge locations worldwide
- **Content Caching**: CloudFront caches content at edge locations
- **Traffic Absorption**: Edge network can absorb large attack volumes
- **Geographic Distribution**: Attacks must hit multiple locations

### AWS Network Protection Services

#### Security Groups

##### What are Security Groups?
- **Virtual Firewall**: Controls traffic to and from AWS resources
- **Instance-Level Protection**: Acts as a firewall for EC2 instances
- **Stateful**: Automatically allows return traffic
- **Default Deny**: All inbound traffic is blocked by default

##### Key Characteristics:

###### Stateful Nature:
- **Inbound Rules**: If you allow inbound traffic, return traffic is automatically allowed
- **Outbound Rules**: If you allow outbound traffic, response traffic is automatically allowed
- **No Need for Symmetric Rules**: Don't need separate rules for response traffic

###### Rule Evaluation:
- **All Rules Evaluated**: All rules are considered before allowing traffic
- **No Rule Priority**: All rules are applied (unlike traditional firewalls)
- **Explicit Allow**: Only traffic specifically allowed can pass
- **Default Deny**: No implied allow rules

##### Security Group Rules:

###### Components:
- **Protocol**: TCP, UDP, ICMP, etc.
- **Port Range**: Specific ports or range of ports
- **Source/Destination**: IP addresses, CIDR blocks, or other security groups
- **Allow Only**: Only allow rules (no deny rules)

###### Examples:
Web Server Security Group:

Allow HTTP (port 80) from 0.0.0.0/0 (internet)

Allow HTTPS (port 443) from 0.0.0.0/0 (internet)

Allow SSH (port 22) from 192.168.1.0/24 (internal network)

Database Security Group:

Allow MySQL (port 3306) from Web Server Security Group

No direct internet access

#### Elastic Load Balancing (ELB)

##### What is Elastic Load Balancing?
- **Traffic Distribution**: Automatically distributes incoming traffic across multiple targets
- **High Availability**: Routes traffic only to healthy instances
- **Scalability**: Scales with your application's traffic
- **Security Integration**: Works with other AWS security services

##### How ELB Helps with Protection:

###### Traffic Distribution:
- **Spread Load**: Distributes attack traffic across multiple instances
- **Prevents Overload**: No single instance gets overwhelmed
- **Auto Scaling Integration**: Can trigger scaling during high traffic
- **Absorption**: Large-scale infrastructure can absorb significant traffic

###### Health Checks:
- **Instance Monitoring**: Regularly checks health of registered instances
- **Automatic Failover**: Stops sending traffic to unhealthy instances
- **Application Awareness**: Can check application-level health, not just server
- **Fast Recovery**: Quickly redirects traffic when instances recover

###### Security Features:
- **SSL/TLS Termination**: Offloads encryption/decryption
- **Sticky Sessions**: Optional session persistence
- **Cross-Zone Load Balancing**: Distributes traffic across all AZs
- **Integration with WAF**: Can work with AWS WAF for application protection

##### Load Balancer Types:

| Type | Best For | Key Features |
|------|----------|--------------|
| **Application Load Balancer** | HTTP/HTTPS traffic | Path-based routing, host-based routing, WebSockets |
| **Network Load Balancer** | TCP/UDP traffic | Ultra-low latency, static IP addresses |
| **Gateway Load Balancer** | Third-party appliances | Inline traffic inspection, security appliances |

#### AWS Regions

##### Geographic Isolation:
- **Physical Separation**: Each Region is physically separate
- **Independent Infrastructure**: No shared components between Regions
- **Attack Isolation**: DDoS attack affects only targeted Region
- **Multi-Region Architecture**: Critical applications can run in multiple Regions

##### Regional Benefits for Security:

###### Geographic Diversity:
- **Distributed Risk**: Attack on one Region doesn't affect others
- **Compliance**: Data can stay in specific geographic areas
- **Latency**: Serve users from nearest Region
- **Redundancy**: Full failover capability between Regions

###### Traffic Management:
- **Route 53**: DNS-level traffic routing between Regions
- **Global Accelerator**: Optimize traffic routing globally
- **CloudFront**: Edge caching reduces load on origin Regions
- **Geographic Restrictions**: Block traffic from specific regions if needed

## AWS Security Services for Network Protection

### AWS Shield

#### Overview:
- **DDoS Protection Service**: Protects AWS resources from DDoS attacks
- **Two Tiers**: Standard (free) and Advanced (paid)
- **Automatic Protection**: Works without configuration
- **Integrated**: Works with CloudFront, Route 53, and ELB

#### AWS Shield Standard

##### What is Shield Standard?
- **Free Service**: Automatically included for all AWS customers
- **Basic Protection**: Protects against common, frequently occurring DDoS attacks
- **No Configuration**: Works automatically, no setup required
- **Network Layer Protection**: Protects at layers 3 and 4 (network and transport)

##### Protection Capabilities:

###### Detection:
- **Traffic Analysis**: Monitors incoming traffic patterns
- **Anomaly Detection**: Identifies unusual traffic volumes
- **Signature-Based**: Recognizes known attack patterns
- **Real-Time Analysis**: Continuous monitoring of network traffic

###### Mitigation:
- **Automatic Response**: Immediately responds to detected attacks
- **Inline Mitigation**: Filters malicious traffic before it reaches resources
- **Scrubbing**: Removes malicious traffic while allowing legitimate traffic
- **No Performance Impact**: Mitigation happens without affecting normal traffic

##### Attack Types Mitigated:
- **SYN Floods**: TCP SYN flood attacks
- **UDP Floods**: UDP reflection and amplification attacks
- **ICMP Floods**: Ping floods and other ICMP-based attacks
- **Other Layer 3/4 Attacks**: Common network-layer DDoS attacks

#### AWS Shield Advanced

##### What is Shield Advanced?
- **Paid Service**: Additional cost for enhanced protection
- **Comprehensive Protection**: Detects and mitigates sophisticated DDoS attacks
- **24/7 Support**: Access to AWS DDoS Response Team (DRT)
- **Detailed Visibility**: Attack diagnostics and reporting

##### Additional Capabilities:

###### Enhanced Detection:
- **Application Layer Detection**: Protects against layer 7 (application) attacks
- **Advanced Analytics**: More sophisticated traffic analysis
- **Attack Forensics**: Detailed information about attack characteristics
- **Real-Time Visibility**: Enhanced monitoring and alerting

###### Advanced Mitigation:
- **Complex Attack Mitigation**: Handles sophisticated multi-vector attacks
- **AWS WAF Integration**: Can work with WAF rules for application protection
- **Custom Mitigations**: Work with DRT to create custom responses
- **Cost Protection**: Fee protection for scaling during attacks

###### Key Features:

##### DDoS Response Team (DRT):
- **Expert Support**: AWS security experts available 24/7
- **Attack Assistance**: Help during active attacks
- **Custom Mitigations**: Create tailored protection rules
- **Proactive Engagement**: Can engage during detected attacks

##### Financial Protection:
- **Cost Protection**: Shield against scaling charges during attacks
- **Fee Coverage**: AWS may cover costs from attack-induced scaling
- **SLA Coverage**: Service level agreement protection
- **Predictable Costs**: Financial protection during incidents

##### Integration Benefits:
- **CloudFront Integration**: Protect content delivery networks
- **Route 53 Integration**: Protect DNS infrastructure
- **ELB Integration**: Protect load-balanced applications
- **Global Accelerator**: Protect globally distributed applications

### AWS WAF (Web Application Firewall)

#### What is AWS WAF?
- **Web Application Firewall**: Protects web applications from common web exploits
- **Application Layer Protection**: Works at layer 7 (application layer)
- **Rule-Based**: Uses configurable rules to filter traffic
- **Integration**: Works with CloudFront, ALB, API Gateway

#### How AWS WAF Works:

##### Web Access Control Lists (Web ACLs):
- **Rule Container**: Web ACLs contain rules that evaluate web requests
- **Default Action**: Allow or block requests that don't match any rule
- **Rule Priority**: Rules are evaluated in order of priority
- **Regional/Global**: Can be regional or CloudFront global

##### Rule Evaluation Process:

Incoming Request → Web ACL → Check Rules in Order
↓
If Blocked → Deny Access
↓
If Allowed → Forward to Application


#### Key Components:

##### Conditions:
- **IP Address**: Allow or block specific IP addresses or ranges
- **Country**: Geographic location of the requester
- **Request Size**: Size limits for HTTP requests
- **SQL Injection**: Patterns that indicate SQL injection attempts
- **Cross-Site Scripting (XSS)** : Patterns that indicate XSS attempts
- **String Matching**: Specific strings in requests
- **Regex Matching**: Regular expression patterns

##### Rules:
- **Rule Type**: Regular or rate-based rules
- **Action**: Allow, block, or count matching requests
- **Conditions**: One or more conditions to check
- **Priority**: Order in which rules are evaluated

##### Rate-Based Rules:
- **Purpose**: Limit requests from specific IP addresses
- **Threshold**: Define maximum requests per minute per IP
- **Use Case**: Mitigate brute-force attacks, application-layer DDoS
- **Automatic Blocking**: IPs exceeding threshold are temporarily blocked

#### Common Protection Scenarios:

##### IP Reputation Blocking:
- **Threat Intelligence**: Block known malicious IP addresses
- **Managed Rules**: AWS provides managed IP reputation lists
- **Custom Lists**: Add your own known-bad IPs
- **Geographic Blocking**: Block traffic from specific countries

##### SQL Injection Prevention:
- **Pattern Detection**: Identify SQL injection attempts in requests
- **Common Signatures**: Detect typical SQL injection patterns
- **Body Inspection**: Check POST data for malicious SQL
- **URL Inspection**: Check query strings for SQL injection

##### Cross-Site Scripting Prevention:
- **Script Detection**: Identify JavaScript injection attempts
- **HTML Inspection**: Check for malicious HTML tags
- **Attribute Inspection**: Look for dangerous attributes like onload
- **Encoding Evasion**: Detect encoded XSS attempts

##### Brute Force Protection:
- **Rate Limiting**: Limit login attempts from single IP
- **Path-Based Limits**: Different limits for different URLs
- **Session Tracking**: Track and limit by session
- **CAPTCHA Integration**: Challenge suspicious requests

#### AWS WAF + Shield Integration:

##### Combined Protection:
- **Layered Defense**: Shield for network layer, WAF for application layer
- **DDoS Mitigation**: Shield handles volumetric attacks, WAF handles application attacks
- **Unified Management**: Manage both through AWS console
- **Comprehensive Coverage**: Full protection from layers 3 through 7

##### Custom Rules for DDoS:
- **Traffic Profiling**: Create rules based on normal traffic patterns
- **Attack-Specific Rules**: Custom rules for specific attack types
- **Rate Limiting**: Prevent application-layer DDoS
- **Challenge Responses**: Require CAPTCHA for suspicious traffic

## Comprehensive Protection Strategy

### Layered Defense Approach:

#### Infrastructure Layer (AWS Built-in):

Shield Standard (Free) → Basic DDoS Protection → Network Layer Attacks
Shield Advanced (Paid) → Sophisticated Attacks → 24/7 Response Team

#### Compute Layer (Security Groups):

Security Groups → Instance-Level Firewall → Stateful Inspection

#### Application Layer (AWS WAF):

AWS WAF → Web ACLs → Rules → Application Layer Protection
#### Traffic Distribution (ELB):

Elastic Load Balancing → Distribute Traffic → Health Checks → Auto Scaling
### Defense in Depth Example:

Internet Traffic
↓
AWS Global Infrastructure (Edge Locations, Regions)
↓
AWS Shield (DDoS Protection)
↓
AWS WAF (Web Application Firewall)
↓
Elastic Load Balancing (Traffic Distribution)
↓
Security Groups (Instance Firewall)
↓
Application (EC2, Lambda, etc.)


## Exam Critical Points

### Must Remember Attack Types:

#### DoS (Denial of Service):
- **Single Source**: One computer attacking
- **Flood Traffic**: Overwhelms with excessive traffic
- **Resource Exhaustion**: Consumes all server resources

#### DDoS (Distributed Denial of Service):
- **Multiple Sources**: Many infected computers (zombie bots)
- **Botnet**: Network of compromised devices
- **Much Larger Scale**: Harder to block due to many IPs

### AWS Protection Layers:

#### Infrastructure Protection:
- **Security Groups**: Instance-level firewall (stateful)
- **ELB**: Distributes traffic, health checks
- **Multiple Regions/AZs**: Geographic distribution makes attacks harder

#### Service Protection:
- **AWS Shield Standard**: Free, automatic DDoS protection
- **AWS Shield Advanced**: Paid, sophisticated DDoS protection, DRT access
- **AWS WAF**: Application layer firewall, web ACLs, rules

### Key Service Features:

#### AWS Shield Standard:
- Free for all AWS customers
- Automatic protection against common DDoS attacks
- Network layer (layers 3/4) protection
- No configuration required

#### AWS Shield Advanced:
- Paid service with enhanced protection
- Application layer (layer 7) protection
- 24/7 access to DDoS Response Team (DRT)
- Detailed attack diagnostics and financial protection

#### AWS WAF:
- Web application firewall (layer 7)
- Web ACLs contain rules
- Rules evaluate requests (allow/block/count)
- Can block based on IP, country, request size, SQL injection, XSS
- Rate-based rules for brute force protection

### Common Exam Scenarios:

#### DDoS Protection Questions:
- "What protects against common DDoS attacks?" → AWS Shield Standard
- "Need sophisticated DDoS protection with expert support?" → AWS Shield Advanced
- "Protecting web application from SQL injection?" → AWS WAF

#### Security Group Questions:
- "Stateful firewall at instance level?" → Security Groups
- "Automatically allows return traffic?" → Security Groups (stateful)
- "Default deny inbound?" → Security Groups

#### Web ACL Questions:
- "What evaluates web requests against rules?" → Web ACLs (in AWS WAF)
- "Rate limiting login attempts?" → AWS WAF rate-based rules
- "Block traffic from specific country?" → AWS WAF geographic condition

### Best Practices Summary:
1. **Use Security Groups**: Implement least privilege for instance access
2. **Enable Shield Standard**: Free basic DDoS protection
3. **Consider Shield Advanced**: For critical applications, compliance needs
4. **Implement AWS WAF**: Protect web applications from common exploits
5. **Distribute with ELB**: Load balancing adds resilience
6. **Multi-Region Architecture**: Critical apps should span Regions
7. **Regular Testing**: Test your protection with simulated attacks
8. **Monitor and Alert**: Use CloudWatch for DDoS alarms


# Protecting Data

## Data Encryption Basics

### What is Encryption?
- **Lock and Key Mechanism**: Protects data like a lock protects valuables
- **Encryption Key**: Turns readable data into randomized characters
- **Decryption Key**: Unlocks data back to readable format
- **Access Control**: Only those with the right key can access the data

### Example:
Customer Profile (readable)
→ Encryption Key → "8f3k9d2j5s" (encrypted)
→ Decryption Key → Customer Profile (readable again)

## Types of Data Encryption

### 1. Data Encryption at Rest

#### Definition:
- **Data is idle**: Stored on disk, not moving
- **Examples**: Data in databases, S3 buckets, EBS volumes
- **Purpose**: Protects against unauthorized access to stored data

#### Where It's Used:
- Amazon S3 buckets
- Amazon EBS volumes
- Amazon DynamoDB tables
- Amazon RDS databases
- Backup files and snapshots

### 2. Data Encryption in Transit

#### Definition:
- **Data is moving**: Traveling between locations
- **Examples**: Data sent from database to application, user to website
- **Purpose**: Prevents interception during transmission

#### SSL/TLS Certificates:
- **SSL/TLS**: Secure Sockets Layer / Transport Layer Security
- **Function**: Establish encrypted network connections
- **Visual Cue**: Padlock icon in browser address bar
- **Result**: Data is encrypted while traveling over networks

## AWS Built-in Data Protection

### Services with Built-in Encryption:

#### Amazon S3
- **Server-Side Encryption**: Automatically encrypts data at rest
- **Options**: SSE-S3, SSE-KMS, SSE-C
- **Bucket Policies**: Can enforce encryption for all uploads

#### Amazon EBS
- **Encrypted Volumes**: EBS volumes can be encrypted
- **Snapshots**: Encrypted snapshots from encrypted volumes
- **Data at Rest**: Protects data on EBS storage

#### Amazon DynamoDB
- **Encryption at Rest**: Automatically encrypted
- **Default**: All DynamoDB tables are encrypted
- **AWS Managed Keys**: Default encryption with AWS owned keys

## AWS Data Protection Services

### AWS Key Management Service (KMS)

#### What is KMS?
- **Key Creation and Management**: Create and manage cryptographic keys
- **Centralized Control**: Single place to manage all encryption keys
- **Integration**: Works with many AWS services
- **Secure**: Keys never leave AWS KMS

#### Key Features:

##### Key Management:
- **Create Keys**: Generate cryptographic keys
- **Rotate Keys**: Automatically rotate keys on schedule
- **Disable Keys**: Temporarily prevent key usage
- **Delete Keys**: Permanently remove keys (with waiting period)

##### Access Control:
- **IAM Integration**: Specify which users/roles can manage keys
- **Key Policies**: Define permissions directly on keys
- **Granular Control**: Different permissions for different keys
- **Audit Trail**: CloudTrail logs all key usage

##### How It Works:
Application wants to encrypt data → Requests key from KMS
KMS provides encrypted data key → Application encrypts data
To decrypt: Application requests decryption from KMS


#### Use Cases:
- **S3 Encryption**: Use KMS keys for S3 server-side encryption
- **EBS Encryption**: Encrypt EBS volumes with KMS keys
- **RDS Encryption**: Encrypt database storage
- **Custom Applications**: Encrypt application data programmatically

### Amazon Macie

#### What is Macie?
- **Sensitive Data Discovery**: Finds sensitive data in S3
- **ML-Powered**: Uses machine learning to identify data types
- **Continuous Monitoring**: Regularly scans S3 buckets
- **Compliance Focus**: Helps meet regulatory requirements

#### What It Detects:
- **PII (Personally Identifiable Information)** : Names, addresses, SSNs
- **Financial Data**: Credit card numbers, bank accounts
- **Credentials**: Passwords, API keys
- **Intellectual Property**: Source code, confidential documents

#### Key Features:

##### Data Discovery:
- **Automated Scanning**: Continuously scans S3 buckets
- **ML Classification**: Learns to identify different data types
- **Custom Identifiers**: Define your own sensitive data patterns
- **Bucket-Level Assessment**: Evaluates security posture of buckets

##### Security Assessment:
- **S3 Security Analysis**: Checks bucket permissions and settings
- **Findings Dashboard**: View all sensitive data discoveries
- **Severity Ratings**: Prioritize most critical findings
- **Remediation Steps**: Guidance on fixing issues

##### Compliance Benefits:
- **GDPR Compliance**: Identify personal data of EU citizens
- **HIPAA Compliance**: Find protected health information
- **PCI DSS**: Detect credit card data for PCI compliance
- **Audit Reports**: Generate compliance documentation

#### Use Cases:
- **Data Inventory**: Know what sensitive data you have
- **Compliance Monitoring**: Ensure compliance with regulations
- **Security Posture**: Identify exposed sensitive data
- **Data Classification**: Automatically classify data types

### AWS Certificate Manager (ACM)

#### What is ACM?
- **SSL/TLS Certificate Management**: Centralized certificate handling
- **Provision and Deploy**: Create certificates for AWS services
- **Automatic Renewal**: Renews certificates before expiration
- **Integration**: Works with CloudFront, ELB, API Gateway

#### Key Features:

##### Certificate Provisioning:
- **Request Certificates**: Create new SSL/TLS certificates
- **Import Certificates**: Bring existing certificates to ACM
- **Public Certificates**: For internet-facing applications
- **Private Certificates**: For internal applications (with ACM Private CA)

##### Lifecycle Management:
- **Automatic Renewal**: ACM renews certificates before expiration
- **Domain Validation**: Verifies domain ownership
- **Deployment**: Attach certificates to AWS services
- **Expiration Alerts**: Notifications before certificates expire

##### Integration:
- **CloudFront**: SSL/TLS for content delivery
- **Application Load Balancer**: HTTPS for load-balanced apps
- **API Gateway**: Secure API endpoints
- **CloudFormation**: Deploy certificates with infrastructure as code

#### Benefits:
- **Reduced Manual Work**: No need to track certificate expiration
- **Centralized Management**: All certificates in one place
- **Cost Effective**: No charge for public certificates
- **Improved Security**: Automatic renewal prevents expired certificates

## Data Protection Summary

### Encryption Methods:
At Rest: Stored data (S3, EBS, DynamoDB)
In Transit: Moving data (SSL/TLS certificates)

### Service Roles:

| Service | Purpose | Key Feature |
|---------|---------|-------------|
| **KMS** | Key management | Create, manage, control cryptographic keys |
| **Macie** | Sensitive data discovery | Find PII and sensitive data in S3 |
| **ACM** | Certificate management | SSL/TLS certificate provisioning and renewal |

### Built-in Protection:
- **S3**: Server-side encryption options
- **EBS**: Encrypted volumes and snapshots
- **DynamoDB**: Automatic encryption at rest

## Exam Critical Points

### Must Remember Definitions:
- **Encryption at Rest**: Data stored on disk (databases, S3, EBS)
- **Encryption in Transit**: Data moving over networks (SSL/TLS)
- **Cryptographic Key**: Random string of digits for encrypting/decrypting

### Key Service Functions:

#### KMS:
- **Create and manage keys**
- **Keys never leave KMS**
- **Control key usage** with IAM and key policies
- **Temporarily disable keys**

#### Macie:
- **Discover sensitive data** in S3
- **Uses ML** to identify data types
- **Helps with compliance** (GDPR, HIPAA, PCI)
- **Assesses S3 security posture**

#### ACM:
- **Manages SSL/TLS certificates**
- **Automatic renewal** before expiration
- **Integrates** with CloudFront, ELB, API Gateway
- **Centralized certificate management**

### Common Exam Scenarios:

- **Need to create encryption keys?** → AWS KMS
- **Find sensitive data in S3?** → Amazon Macie
- **Manage SSL/TLS certificates?** → AWS Certificate Manager
- **Encrypt EBS volume?** → Use KMS keys (built-in EBS encryption)
- **Data moving between systems?** → Encryption in transit (SSL/TLS)

### Best Practices:
1. **Encrypt everything**: Enable encryption at rest by default
2. **Use KMS**: Centralize key management
3. **Monitor with Macie**: Know where sensitive data lives
4. **Use ACM**: Automate SSL/TLS certificate management
5. **Least privilege**: Limit who can access keys
6. **Rotate keys**: Regularly rotate encryption keys
7. **Enable CloudTrail**: Audit key usage and certificate actions

# Detecting and Responding to Security Incidents

## Overview
- **Prevention + Detection**: Both are essential for complete security
- **Response Readiness**: Be prepared to detect and respond when incidents occur
- **AWS Services**: Multiple services for detection, investigation, and response

## Amazon Inspector

### What is Amazon Inspector?
- **Automated Security Assessments**: Scans EC2 instances, containers, and Lambda functions
- **Vulnerability Detection**: Finds security vulnerabilities and deviations from best practices
- **Continuous Monitoring**: Regularly checks your resources

### What It Checks For:
- **Open Access**: Unrestricted access to EC2 instances
- **Vulnerable Software**: Outdated or vulnerable software versions
- **Security Best Practices**: Deviations from recommended configurations

### Key Features:
- **Prioritized Findings**: Issues ranked by severity level
- **Detailed Descriptions**: Each finding includes explanation and fix recommendations
- **Console Access**: View all assessments in Inspector console
- **API Access**: Retrieve findings programmatically

### Use Cases:
- **Compliance Checks**: Verify resources meet security standards
- **Vulnerability Management**: Identify and fix security gaps
- **CI/CD Integration**: Scan during development pipeline

## Amazon GuardDuty

### What is GuardDuty?
- **Intelligent Threat Detection**: Identifies threats across AWS infrastructure
- **Continuous Monitoring**: Analyzes account metadata and network activity streams
- **Multiple Detection Methods**: Uses known malicious IPs, anomaly detection, and ML

### How It Works:

AWS Environment → GuardDuty Monitoring → Threat Detection → Findings

### Detection Methods:
- **Known Malicious IPs**: Compares traffic against threat intelligence feeds
- **Anomaly Detection**: Identifies unusual behavior patterns
- **Machine Learning**: Improves detection accuracy over time

### Key Features:
- **Detailed Findings**: Each threat includes description and remediation steps
- **Automated Response**: Can trigger Lambda functions for remediation
- **Integrated**: Works with other AWS security services
- **Continuous**: Monitors 24/7 without manual intervention

### Use Cases:
- **Account Compromise**: Detect unauthorized access
- **Instance Compromise**: Identify compromised EC2 instances
- **Cryptocurrency Mining**: Detect crypto mining activity
- **Reconnaissance**: Identify attacker scanning activities

## Amazon Detective

### What is Detective?
- **Investigation Tool**: Analyzes root cause of security findings
- **Post-Detection**: Used AFTER GuardDuty or other services detect a threat
- **Visual Analysis**: Interactive visualizations for investigation

### Key Features:
- **Interactive Visualizations**: See resource and user interactions graphically
- **Configurable Timeline**: Investigate activity over specific time periods
- **Unified View**: All investigation data in one console
- **Remediation Steps**: Includes recommended actions

### How It Helps:
- **Root Cause Analysis**: Understand why a security issue occurred
- **Scope Assessment**: Determine which resources were affected
- **Timeline Reconstruction**: See sequence of events leading to incident
- **Faster Investigation**: Visual tools speed up analysis

### Use Cases:
- **Incident Investigation**: Deep dive into security findings
- **Forensic Analysis**: Understand attack vectors and methods
- **Compliance Reporting**: Document investigation results

## AWS Security Hub

### What is Security Hub?
- **Centralized Security View**: Aggregates findings from multiple AWS services
- **Single Dashboard**: Comprehensive security and compliance status
- **Automated Aggregation**: Collects findings from AWS and partner services

### Key Features:
- **Unified Findings**: All security alerts in one place
- **Insights**: Actionable groupings of related findings
- **Automated Remediation**: Can trigger responses to issues
- **Compliance Checks**: Automated compliance standards verification

### How It Works:

AWS Services (GuardDuty, Inspector, etc.) → Security Hub → Unified Dashboard
Partner Services → Security Hub → Insights & Remediation


### Benefits:
- **Accelerated TTR**: Time to Resolution improved with automated remediation
- **Comprehensive View**: See entire security posture at once
- **Prioritized Issues**: Focus on most important findings first
- **Cross-Account Visibility**: View security across multiple accounts

### Use Cases:
- **Security Posture Management**: Track overall security health
- **Compliance Monitoring**: Verify compliance with standards (CIS, PCI, etc.)
- **Centralized Alerting**: All security alerts in one place

## Service Comparison

| Service | Purpose | When to Use |
|---------|---------|-------------|
| **Inspector** | Vulnerability scanning | Find weaknesses in EC2, containers, Lambda |
| **GuardDuty** | Threat detection | Identify active threats in real-time |
| **Detective** | Investigation | Analyze root cause after detection |
| **Security Hub** | Centralized view | Aggregate all security findings |

## How They Work Together

### Complete Security Workflow:

1. PREVENTION: IAM, WAF, Shield (stop attacks)
↓

2. VULNERABILITY SCANNING: Inspector (find weaknesses)
↓

3. THREAT DETECTION: GuardDuty (identify active threats)
↓

4. INVESTIGATION: Detective (analyze root cause)
↓

5. CENTRALIZED VIEW: Security Hub (aggregate all findings)
↓

6. RESPONSE: Automated or manual remediation


### Example Scenario:
GuardDuty detects unusual API activity
↓
Security Hub aggregates the finding with other alerts
↓
Security team uses Detective to investigate root cause
↓
Findings show an EC2 instance with vulnerability (found by Inspector)
↓
Team remediates the issue
↓
Security Hub shows resolved status


## Exam Critical Points

### Must Remember Each Service:

#### Amazon Inspector:
- **Vulnerability scanner** for EC2, containers, Lambda
- Checks for **open access** and **vulnerable software**
- Provides **prioritized findings** with fix recommendations

#### Amazon GuardDuty:
- **Intelligent threat detection**
- Uses **ML, anomaly detection, and known malicious IPs**
- Continuous monitoring of **account metadata and network activity**

#### Amazon Detective:
- **Investigation tool** for root cause analysis
- **Interactive visualizations** with timelines
- Used **after** a threat is detected

#### AWS Security Hub:
- **Centralized dashboard** for security findings
- Aggregates from **AWS and partner services**
- Creates **insights** and enables **automated remediation**

### Common Exam Scenarios:

- **Need to find vulnerabilities?** → Amazon Inspector
- **Need real-time threat detection?** → Amazon GuardDuty
- **Need to investigate a detected threat?** → Amazon Detective
- **Need one place to see all security findings?** → AWS Security Hub

### Key Differentiators:
- **Inspector = Proactive** (find weaknesses before they're exploited)
- **GuardDuty = Reactive** (detect ongoing threats)
- **Detective = Investigative** (understand what happened)
- **Security Hub = Aggregator** (see everything in one place)

### Best Practices:
1. **Enable GuardDuty** for continuous threat monitoring
2. **Run Inspector assessments** regularly to find vulnerabilities
3. **Use Detective** when investigating security findings
4. **Set up Security Hub** for centralized visibility
5. **Automate responses** where possible (Lambda + Security Hub)
6. **Review findings regularly** and prioritize by severity
