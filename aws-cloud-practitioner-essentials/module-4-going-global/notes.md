Module 4: Going Global - AWS Global Infrastructure
🌍 AWS Global Infrastructure Overview

# Module 4: Going Global - AWS Global Infrastructure

## 🌍 Introduction to Going Global

### 🗺️ How to Choose a Region or Set of Regions

**Meaning:** Selecting the right AWS regions based on specific business and technical requirements to optimize performance, cost, compliance, and availability.

**Key Factors to Consider:**

1. **Latency & Proximity:**
   - Choose regions closest to your user base
   - Lower latency = better user experience
   - **Example:** If most users are in Europe, choose `eu-west-1` (Ireland) or `eu-central-1` (Frankfurt)

2. **Cost Optimization:**
   - Different regions have different pricing
   - Some services are cheaper in specific regions
   - **Example:** US East (N. Virginia) often has the lowest prices and newest services

3. **Compliance & Legal Requirements:**
   - Data sovereignty laws may require data to stay in specific countries
   - Industry regulations (GDPR, HIPAA, etc.)
   - **Example:** German company might choose `eu-central-1` to comply with EU data protection laws

4. **Service Availability:**
   - Not all services are available in all regions
   - Newer services launch in select regions first
   - **Example:** Some AI/ML services may only be in `us-east-1` initially

5. **Disaster Recovery:**
   - Choose geographically separate regions for backup
   - Ensure business continuity
   - **Example:** Primary in `us-east-1`, backup in `us-west-2` (Oregon)

**Real-World Scenario: E-commerce Company Expansion**
- **Current:** Serving US customers from `us-east-1`
- **Expansion:** Planning to enter European market
- **Decision:** Deploy in `eu-west-1` for:
  - Lower latency for European customers
  - GDPR compliance
  - Cost-effective European pricing
  - Geographic separation from US infrastructure

### 📍 AWS Edge Locations

**Meaning:** Physical data centers deployed in major cities worldwide that cache content to reduce latency for end users.

**Key Characteristics:**
- **Not full AWS regions** - only cache content
- **Used by CloudFront (CDN)** and Route 53
- **Global network** - 400+ locations in 90+ cities
- **Reduce latency** by serving content closer to users

**How They Work:**
1. User requests content from your website
2. Request routed to nearest edge location
3. If content is cached, served immediately
4. If not cached, fetched from origin and cached for future requests

**Real-World Example: Video Streaming Service**
- **Origin Server:** Main video files stored in `us-east-1`
- **Edge Locations:** Cache popular videos in Tokyo, London, São Paulo
- **User in Tokyo:** Gets video from Tokyo edge location (20ms latency)
- **Instead of:** Fetching from US East (200ms+ latency)

**Benefits:**
- ⚡ **Faster load times** for global users
- 📉 **Reduced origin server load**
- 💰 **Lower data transfer costs**
- 🌐 **Improved global user experience**

### 🏗️ Infrastructure as Code (IaC) and AWS CloudFormation

**Meaning:** Managing and provisioning cloud infrastructure through machine-readable definition files, rather than manual configuration.

**AWS CloudFormation:** AWS's native Infrastructure as Code service that allows you to model, provision, and manage AWS resources using templates.

**Key Concepts:**

**Infrastructure as Code (IaC):**
- **Treat infrastructure like software code**
- **Version control** your infrastructure
- **Automate deployments** and updates
- **Ensure consistency** across environments

**AWS CloudFormation Templates:**
- **JSON or YAML files** defining AWS resources
- **Declarative approach** - you define what you want, AWS figures out how
- **Repeatable deployments** - create identical stacks multiple times

**Real-World Example: Web Application Deployment**

**Traditional Approach:**
1. Manual EC2 instance creation
2. Manual security group configuration
3. Manual load balancer setup
4. Manual database configuration
5. **Result:** Inconsistent, error-prone, time-consuming

**CloudFormation Approach:**
``yaml
# web-app-template.yaml
Resources:
  WebServer:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: ami-0abcdef1234567890
      InstanceType: t2.micro
      SecurityGroups:
        - !Ref WebSecurityGroup
  
  WebSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Enable HTTP access
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0
Deployment Command:
aws cloudformation create-stack \
  --stack-name my-web-app \
  --template-body file://web-app-template.yaml

Benefits of CloudFormation:

🔄 Consistent environments (dev, staging, production)

⚡ Rapid provisioning (minutes instead of hours)

🛡️ Reduced human error

📊 Version control and change tracking

🗑️ Easy cleanup (delete stack removes all resources)

Use Case: Multi-Region Deployment

Template defines complete application stack

Deploy to multiple regions with same template

Ensure consistency across global deployment

Automate disaster recovery setup

🎯 Why Going Global Matters
Business Impact:

🌐 Reach global customers with low latency

💰 Optimize costs by choosing right regions

🛡️ Ensure compliance with local regulations

🔄 Maintain availability during regional outages

Technical Benefits:

⚡ Improved performance through edge caching

🔧 Infrastructure consistency with IaC

📈 Scalability to handle global traffic

🛡️ Disaster recovery capabilities


🗺️ AWS Regions
Meaning: Separate geographic areas that consist of multiple isolated Availability Zones.

Key Characteristics:

Physically separate from other regions

Each region has multiple Availability Zones

Choose regions based on: latency, cost, compliance, service availability

Not all services are available in all regions

Example:

us-east-1 (N. Virginia) - Largest region, most services

eu-west-1 (Ireland) - Serves European customers

ap-southeast-1 (Singapore) - Serves Asia Pacific customers

🏢 Availability Zones (AZs)
Meaning: One or more discrete data centers with redundant power, networking, and connectivity in a Region.

Key Characteristics:

Physically separate within a region

Connected through low-latency links

Designed for fault isolation

Run on independent infrastructure

Example:

us-east-1 has 6 Availability Zones (us-east-1a, us-east-1b, etc.)

Deploy applications across multiple AZs for high availability

📍 Edge Locations
Meaning: Sites that Amazon CloudFront uses to cache copies of content for faster delivery to users.

Key Characteristics:

Located in major cities worldwide

Used by CloudFront (CDN) and Route 53

Reduce latency for end users

Not used for general compute workloads

Example:

CloudFront edge location in Tokyo serves Japanese users

Route 53 uses edge locations for DNS resolution

🚀 Amazon CloudFront
Meaning: A content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds.

How CloudFront Works:
Origin: Your content source (S3 bucket, EC2 instance, etc.)

Distribution: CloudFront configuration that defines how content is delivered

Edge Locations: Global network of servers that cache content

Viewer: End user requesting content

Real-World Example: Global Media Streaming

S3 Bucket (Origin) → CloudFront Distribution → 
Edge Locations (300+ globally) → 
Users (Low latency streaming worldwide)

Benefits:

⚡ Reduced latency for global users

📈 Reduced origin server load

🔒 DDoS protection with AWS Shield

💰 Cost savings on data transfer

🔄 Dynamic content acceleration

🎯 Amazon Route 53
Meaning: A scalable and highly available Domain Name System (DNS) web service designed to give developers and businesses an extremely reliable and cost-effective way to route end users to Internet applications.

Route 53 Routing Policies:
1. Simple Routing
Meaning: Basic DNS routing to a single resource.

Example:

example.com → 192.0.2.1 (single web server)

2. Weighted Routing
Meaning: Route traffic to multiple resources in proportions you specify.

Example:

70% traffic → US-East servers

30% traffic → EU-West servers

Useful for A/B testing or blue-green deployments

3. Latency-Based Routing
Meaning: Route traffic to the region that provides the best latency.

Example:

User in London → EU-West servers

User in Tokyo → AP-Northeast servers

Automatic performance optimization

4. Geolocation Routing
Meaning: Route traffic based on user's geographic location.

Example:

Users in France → French-language content

Users in Germany → German-language content

Compliance with data sovereignty laws

5. Failover Routing
Meaning: Route traffic to a backup resource if the primary is unhealthy.

Example:

Primary: US-East servers

Secondary: EU-West servers (if primary fails)

Automatic disaster recovery

🔄 Global Applications Architecture
High Availability Pattern:

Users → Route 53 (DNS) → CloudFront (CDN) → 
Application Load Balancer → 
EC2 Instances (across multiple AZs) → 
RDS Database (Multi-AZ deployment)

Disaster Recovery Pattern:

Primary Region: Active workload
Secondary Region: Standby environment
Route 53: Automatic failover between regions

💰 Cost Optimization for Global Services
CloudFront Pricing:
Data Transfer Out: Varies by region

Requests: Number of HTTP/HTTPS requests

Invalidation Requests: Clearing cache

Route 53 Pricing:
Hosted Zones: Monthly charge per zone

Queries: Number of DNS queries

Health Checks: Monitoring endpoints

Optimization Strategies:
Use CloudFront to reduce origin data transfer costs

Choose appropriate regions based on pricing

Use Route 53 latency-based routing for performance

Implement caching strategies to reduce requests

🛡️ Security Considerations
Global Infrastructure Security:
DDoS Protection: AWS Shield with CloudFront

SSL/TLS: Custom SSL certificates with CloudFront

DNS Security: DNSSEC with Route 53

Data Sovereignty: Choose regions for compliance

Best Practices:
Enable AWS WAF with CloudFront

Use Route 53 for DNS failover

Implement geographic restrictions if needed

Monitor with CloudWatch and AWS X-Ray

🧪 Hands-On Practice
Created CloudFront distribution for static website

Configured Route 53 with weighted routing policy

Set up latency-based routing for global application

Implemented failover routing for disaster recovery

✅ Completed on:


