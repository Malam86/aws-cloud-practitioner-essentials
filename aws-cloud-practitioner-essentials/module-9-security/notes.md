Module 9: Introduction to Security on AWS
📁 Module 9 - Security Notes
1. Authentication vs Authorization
Authentication (WHO you are)
Definition: Verifying the identity of a user or entity through credentials

Common credentials: Username/password, MFA tokens, biometrics

Question it answers: "Are you who you claim to be?"

Real-world example: Logging into a portal with your username and password

Authorization (WHAT you can do)
Definition: Granting users certain access rights and permissions

Determines: Which actions a user can perform in a system or application

Question it answers: "Are you allowed to do this?"

Real-world example: After logging in, an employee can only access their own records, not everyone's records

Quick Comparison Table
Aspect	Authentication	Authorization
Focus	Identity verification	Permission validation
Order	Happens first	Happens after authentication
Analogy	Showing your ID	Your ID determines which rooms you can enter
Example	Logging in with password	Accessing only your own files
2. AWS Shared Responsibility Model
The Core Concept
Security is shared between AWS and the customer. Think of it like renting an apartment:

Landlord (AWS) = Responsible for the building structure, plumbing, electricity

Tenant (You) = Responsible for locking your door, securing your belongings

Customer: Security IN the Cloud
You are responsible for everything you create and manage in AWS

Responsibility	What It Means
Data security	Managing security of your data, systems, and applications
Content control	Deciding what data and workloads to store or run in AWS
Service selection	Determining which AWS services to use
Access management	Controlling who has access to environments and resources
AWS: Security OF the Cloud
AWS is responsible for the infrastructure that runs all services

Responsibility	What It Means
Foundational software	The software that powers AWS services
Virtualization layer	The layer that separates customer instances
Hardware	Servers, storage, networking equipment
Global infrastructure	Regions, Availability Zones, edge locations
Visual Summary
┌─────────────────────────────────────────┐
│  CUSTOMER: Security IN the Cloud        │
│  • Data, systems, applications          │
│  • Access management                     │
│  • Service configuration                 │
├─────────────────────────────────────────┤
│  AWS: Security OF the Cloud             │
│  • Hardware, software, networking       │
│  • Virtualization layer                 │
│  • Global infrastructure (Regions, AZs) │
└─────────────────────────────────────────┘
3. AWS Security Controls
AWS provides security mechanisms to protect your cloud resources in three ways:

1️⃣ Prevent Security Incidents
Proper permission and access management

Set up who can do what before issues happen

Examples: IAM policies, MFA requirements

2️⃣ Protect Resources
Safeguard networks, applications, and data

Create barriers against unauthorized access

Examples: Security groups, encryption, WAF

3️⃣ Detect and Respond
Identify security incidents as they occur

Take action when something suspicious happens

Examples: CloudTrail logging, GuardDuty alerts

📝 Key Takeaways for Exam
Concept	Remember This
Authentication	"Who are you?" - Login credentials
Authorization	"What can you do?" - Permissions after login
Customer Responsible	Everything you create IN the cloud
AWS Responsible	Everything OF the cloud (infrastructure)
Security Controls	Prevent → Protect → Detect & Respond
