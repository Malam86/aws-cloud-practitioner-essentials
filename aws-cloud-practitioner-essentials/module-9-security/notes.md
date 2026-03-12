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


Preventing Unauthorized Access

## AWS Identity and Access Management (IAM)

### Overview
- **Core Security Service**: Manages identities and access to AWS services and resources
- **Default Deny**: By default, all actions are denied in AWS
- **Explicit Permission**: You must explicitly grant permission for any action
- **Centralized Control**: One place to manage users, permissions, and access

### The Principle of Least Privilege

#### Definition:
- **Core Security Concept**: Give people and systems access only to what they need
- **Minimum Required Access**: Provide exactly the permissions necessary and nothing more
- **Risk Reduction**: Limits potential damage if credentials are compromised
- **Operational Best Practice**: Standard security recommendation across all industries

#### Why It Matters:
- **Security Incidents**: Most breaches happen due to excessive permissions
- **Accidental Changes**: Prevent unintended modifications to critical resources
- **Compliance Requirements**: Many regulations require least privilege access
- **Audit Trail**: Easier to track who did what with limited permissions

#### Implementation in IAM:
- **Start with Deny**: All actions denied by default
- **Add Minimal Permissions**: Grant only what's needed for specific tasks
- **Regular Review**: Periodically audit and remove unnecessary permissions
- **Use Groups and Roles**: Organize permissions by job function

### IAM Identities

#### IAM Users

##### What is an IAM User?
- **Individual Identity**: Represents a person or application that needs access to AWS
- **Unique Credentials**: Each user has their own set of credentials
- **Long-term Access**: Users have permanent access until disabled
- **Best Practice**: Avoid using root user, create individual users instead

##### User Credentials:
- **Password**: For AWS Management Console access
- **Access Keys**: For programmatic access (CLI, SDKs, APIs)
- **MFA Devices**: Optional but recommended for additional security
- **SSH Keys**: For CodeCommit and EC2 instances

##### When to Create Users:
- **Employees**: Individual developers, administrators, operators
- **Applications**: Long-running applications needing AWS access
- **Service Accounts**: Automated processes requiring AWS permissions

#### IAM Groups

##### What is an IAM Group?
- **Collection of Users**: Organizes users with similar job functions
- **Permission Inheritance**: Users inherit permissions from their groups
- **Simplified Management**: Change permissions once for entire group
- **No Nesting**: Groups cannot contain other groups

##### Common Group Examples:
- **Admins**: Full access to management functions
- **Developers**: Access to development resources only
- **Analysts**: Read-only access to data and reports
- **Support**: Limited access for troubleshooting

##### Benefits of Groups:
- **Scalability**: Manage hundreds of users efficiently
- **Consistency**: All users in same role have identical permissions
- **Onboarding/Offboarding**: Easy to add/remove users from groups
- **Audit Friendly**: Clear mapping between job roles and permissions

#### IAM Roles

##### What is an IAM Role?
- **Temporary Identity**: Assumed temporarily when needed
- **No Permanent Credentials**: Provides temporary security credentials
- **Trust Relationship**: Defines who can assume the role
- **Permission Policy**: Defines what the role can do

##### Key Characteristics:
- **Time-limited**: Credentials expire automatically (15 minutes to 12 hours)
- **Automatic Rotation**: New credentials issued each session
- **Cross-account Access**: Can be used across different AWS accounts
- **Service Access**: EC2 instances, Lambda functions can assume roles

##### Common Use Cases:
- **EC2 Instance Access**: Give applications on EC2 access to AWS services
- **Cross-account Access**: Allow users in one account to access resources in another
- **Federated Users**: External identity providers accessing AWS
- **AWS Services**: Lambda functions accessing S3, DynamoDB

##### How Roles Work:

User/Service → Assume Role → Temporary Credentials → Access Resources

### IAM Policies

#### What are IAM Policies?
- **JSON Documents**: Written in JSON format defining permissions
- **Permission Rules**: Specify allowed or denied actions on resources
- **Attachable**: Can be attached to users, groups, or roles
- **Composable**: Multiple policies can be attached to one identity

Policy Elements:
Effect:
Allow: Grants permission

Deny: Explicitly denies permission (overrides any Allow)

Action:
Service Prefix: e.g., s3:, ec2:, iam:

Specific Actions: e.g., ListBucket, GetObject, CreateUser

Wildcards: Use * for multiple actions

Resource:
ARN (Amazon Resource Name): Unique identifier for AWS resources

Format: arn:partition:service:region:account:resource

Specific Resources: Target individual buckets, tables, instances

Wildcards: Use * for multiple resources

Condition (Optional):
Context: When the policy applies (IP address, time, MFA status)

Examples:

Source IP address range

Multi-factor authentication present

Current time within business hours

Policy Types:
AWS Managed Policies:
Pre-defined: Created and maintained by AWS

Common Use Cases: AdministratorAccess, ReadOnlyAccess

Automatic Updates: Updated by AWS when needed

Best For: Standard job functions

Customer Managed Policies:
Custom Created: Written by you for specific needs

Full Control: You create, manage, and update

Reusable: Can be attached to multiple identities

Best For: Organization-specific requirements

Inline Policies:
Embedded Directly: Attached to single user, group, or role

One-to-One Relationship: Exists only for that identity

Harder to Manage: No reuse across identities

Best For: Special-case permissions

AWS Account Root User
What is the Root User?
Account Owner: The email address used to create the AWS account

Unlimited Access: Has complete, unrestricted access to all resources

Single Identity: Only one root user per AWS account

Cannot Be Limited: Root user permissions cannot be restricted by IAM

Best Practices for Root User:
DO NOT:
Don't use for daily tasks: Never use root for routine work

Don't share credentials: Keep root user credentials extremely secure

Don't create access keys: Avoid programmatic access as root

Don't use for multiple users: Each person should have their own IAM user

DO:
Enable MFA: Always enable multi-factor authentication on root user

Secure email: Use a strong, monitored email address

Limited use: Only use for specific account management tasks

Create IAM users: Create IAM users for all human access

When to Use Root User:
Account Settings: Changing account name, email, password

Billing Information: Accessing and updating payment methods

Support Plans: Changing AWS Support plan

Restricted Actions: Some administrative tasks require root (e.g., closing account)

IAM Actions: Creating IAM users initially, some service-linked roles

Multi-Factor Authentication (MFA)
What is MFA?
Additional Security Layer: Requires second authentication factor

Something You Know: Password (first factor)

Something You Have: MFA device (second factor)

Drastically Reduces Risk: Even if password stolen, account remains secure

MFA Options:
Virtual MFA Devices:
Authenticator Apps: Google Authenticator, Microsoft Authenticator

Multiple Devices: Can be installed on smartphone or tablet

Cost Effective: Free to use

Supported: Works on any compatible phone

Hardware MFA Devices:
Physical Tokens: Key fobs, USB devices

No Battery Worry: Some have no battery requirements

High Security: Cannot be copied or duplicated

Compliance: Required for some regulatory standards

FIDO Security Keys:
Biometric Options: Fingerprint readers on keys

USB/NFC: Connect via USB or tap for NFC

Phishing Resistant: Modern security standard

Where to Enable MFA:
Root User: Absolutely required

IAM Users: All privileged users

Administrative Groups: Anyone with administrative access

IAM Best Practices
1. Lock Down Root User
Enable MFA on root account

Don't use root for everyday tasks

Don't create access keys for root

Store root credentials securely

2. Create Individual Users
One user per person, not shared accounts

Use groups to assign permissions

Avoid using root for anyone

3. Use Groups for Permissions
Assign permissions to groups, not individuals

Users join groups based on job function

Makes management scalable and consistent

4. Grant Least Privilege
Start with minimal permissions

Add only what's needed for specific tasks

Regularly audit and remove excess permissions

Use conditions to further restrict access

5. Use IAM Roles for Applications
Don't put credentials in code

EC2 instances should assume roles

Lambda functions should use execution roles

Temporary credentials are more secure

6. Enable MFA for All Users
Especially for privileged users

Consider requiring MFA for sensitive actions

Use MFA conditions in policies

7. Rotate Credentials Regularly
Rotate access keys periodically

Remove unused credentials

Don't share access keys

Use AWS Secrets Manager for automation

8. Monitor IAM Activity
Use AWS CloudTrail to track IAM actions

Monitor for unusual activity

Set up alerts for critical changes

Regularly review IAM configuration

Additional Access Management Services
AWS IAM Identity Center
Overview:
Centralized Identity Management: Manages access across AWS accounts and applications

Single Sign-On (SSO) : Users log in once to access multiple resources

Federated Identity: Connects to existing identity sources (Active Directory, Okta, etc.)

Workforce Access: Designed for employees and contractors

Key Features:
Federated Identity Management:
Definition: System allowing users to access multiple applications with single set of credentials

Identity Sources:

AWS Managed Directory: Built-in directory service

Self-managed Active Directory: Connect on-premises AD

External Identity Providers: Okta, Azure AD, Google Workspace

Benefits: Users remember one password, centralized management

Multi-Account Access:
AWS Organizations Integration: Manage access across all accounts in organization

Permission Sets: Define what users can do in each account

Account Assignment: Assign users/groups to specific accounts

Centralized Auditing: Track user activity across all accounts

Application Access:
SSO for Business Apps: Salesforce, Office 365, Slack, etc.

Custom Applications: SAML 2.0 integration for custom apps

AWS Managed Applications: QuickSight, CodeCommit, etc.

User Portal: Single dashboard for all accessible applications

Benefits:
Improved User Experience: One login for everything

Enhanced Security: Centralized control over authentication

Reduced Password Fatigue: Fewer passwords to remember

Simplified On/Offboarding: One place to grant/revoke access

Audit Trail: Comprehensive logging of user activity

AWS Secrets Manager
Overview:
Secure Secret Storage: Manages passwords, API keys, database credentials

Lifecycle Management: Automates rotation of secrets

Fine-grained Access: IAM policies control who can access secrets

Encryption: Automatically encrypts secrets at rest

What Are Secrets?
Definition: Confidential information known only to specific individuals/groups

Examples:

Database passwords and credentials

API keys for third-party services

SSH keys and certificates

OAuth tokens and application secrets

Key Features:
Secure Storage:
Encryption at Rest: Uses AWS KMS for encryption

Encryption in Transit: All API calls use TLS

Access Control: IAM policies restrict who can access secrets

Audit Trail: CloudTrail logs all secret access

Automatic Rotation:
Scheduled Rotation: Automatically change secrets on schedule

Lambda Integration: Custom rotation functions

Database Integration: Built-in rotation for RDS, Redshift, DocumentDB

No Downtime: Applications use new credentials seamlessly

Retrieval:
SDK Integration: Applications retrieve secrets programmatically

Caching: SDKs can cache secrets for performance

Version Tracking: Multiple versions of secrets maintained

Secret References: Use secret ARNs in configuration

Benefits:
Security Improvements:
No Hard-coded Secrets: Never put credentials in code

Centralized Management: All secrets in one secure place

Automatic Rotation: Regularly change secrets without manual work

Access Control: Fine-grained permissions for each secret

Operational Benefits:
Reduced Risk: No exposed credentials in configuration files

Compliance: Meets requirements for secret rotation

Developer Productivity: Easy to retrieve secrets in code

Audit Ready: Complete history of secret access and changes

AWS Systems Manager
Overview:
Centralized Management: Single view for managing AWS resources

Node Management: Manage EC2 instances, on-premises servers, hybrid environments

Automation: Automate operational tasks and patching

Unified Interface: Consistent experience across accounts and regions

Key Concepts:
Nodes:
Definition: Connection points in a network, system, or structure

Examples: EC2 instances, on-premises servers, virtual machines

Management: Systems Manager provides unified node management

Visibility: Central view of all nodes regardless of location

Capabilities:
Inventory Management:
Resource Discovery: Automatically discover all nodes

Configuration Tracking: Track OS, applications, patches

Metadata Collection: Collect system information and details

Centralized View: Single dashboard for all resources

Patch Management:
Automated Patching: Schedule and automate security patches

Compliance Monitoring: Track patch compliance across nodes

Approval Workflows: Control which patches are applied

Reporting: Detailed compliance reports for audits

Automation:
Run Commands: Execute scripts across multiple nodes

State Management: Ensure nodes stay in desired state

Maintenance Windows: Schedule operational tasks

Workflow Automation: Create multi-step automation workflows

Session Manager:
Secure Shell Access: Connect to instances without SSH keys

No Open Ports: No need for open inbound ports

Audit Logging: All sessions logged and audited

IAM Integration: Fine-grained access control

Benefits:
Centralized Control: Manage all resources from one place

Improved Security: No need for permanent SSH keys

Automated Compliance: Ensure all nodes meet security standards

Operational Efficiency: Automate routine tasks

Hybrid Support: Manage on-premises and cloud resources together

Exam Critical Points
Must Remember Definitions:
IAM Basics:
Root User: Account owner, unlimited access, use MFA, avoid daily use

IAM Users: Individual identities for people/applications

IAM Groups: Collections of users for permission management

IAM Roles: Temporary identities for services and cross-account access

IAM Policies: JSON documents defining permissions

Key Concepts:
Principle of Least Privilege: Grant only necessary permissions

Default Deny: All actions denied by default

Explicit Allow: Must specifically grant permission

MFA: Multi-factor authentication for additional security

Additional Services:
IAM Identity Center: Centralized SSO and federated identity

Secrets Manager: Secure storage and rotation of secrets

Systems Manager: Centralized node management and automation

Service Comparison:
Service	Purpose	Key Feature
IAM	Identity and access management	Users, groups, roles, policies
IAM Identity Center	Centralized workforce access	SSO, federation, multi-account
Secrets Manager	Secret storage and rotation	Automatic rotation, encryption
Systems Manager	Node management and automation	Patching, inventory, session manager
Common Exam Scenarios:
Least Privilege Questions:
Look for phrases like "minimum access," "need-to-have," "only what's necessary"

Answer will involve granting limited permissions

Root User Questions:
When should root user be used? Account settings, billing, restricted tasks

How to secure root? Enable MFA, secure email, avoid daily use

IAM Role Questions:
When to use roles? EC2 instances need S3 access, cross-account access

Benefits? Temporary credentials, no hard-coded keys, automatic rotation

MFA Questions:
Why use MFA? Additional security layer, protects even if password stolen

Where required? Root user, privileged IAM users

Security Best Practices Summary:
Root user: Enable MFA, lock down, don't use daily

IAM users: Create individual users, use groups

Least privilege: Grant minimal permissions, audit regularly

Roles: Use for applications and services

MFA: Enable for all users, especially privileged

Secrets Manager: Never hard-code credentials

Systems Manager: Centralize node management and patching

Monitor: Use CloudTrail to track access and changes
