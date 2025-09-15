Module 4: Going Global - AWS Global Infrastructure
🌍 AWS Global Infrastructure Overview
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


