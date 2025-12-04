# Module 9: Security - Key Concepts

## 🔐 AWS Shared Responsibility Model

### AWS Responsibility (Security OF the Cloud)
- **Infrastructure Security**: Physical security of data centers, hardware, networking
- **Foundation Services**: Compute, storage, database, networking infrastructure
- **Software Maintenance**: Host operating systems, virtualization layers
- **Service Availability**: Ensuring services are available and performant

### Customer Responsibility (Security IN the Cloud)
- **Data Classification & Accountability**: What data you store and its sensitivity
- **Platform & Application Management**: OS, network, firewall configurations
- **Identity & Access Management**: User access, permissions, authentication
- **Client-side Data Encryption**: Data encryption, network traffic protection
- **Server-side Encryption**: File system and data encryption
- **Network Traffic Protection**: Security groups, NACLs, VPC configurations

## 👥 Identity and Access Management (IAM)

### Core IAM Components
- **Users**: Individual people or applications that interact with AWS
- **Groups**: Collection of users with similar permissions
- **Roles**: Temporary credentials for AWS services or cross-account access
- **Policies**: JSON documents defining permissions (identity-based & resource-based)

### IAM Policy Types
- **Identity-based Policies**: Attached to users, groups, or roles
- **Resource-based Policies**: Attached to resources (S3 buckets, SNS topics)
- **Permissions Boundaries**: Maximum permissions a user/role can have
- **Service Control Policies (SCPs)**: Organization-level permission boundaries
- **Session Policies**: Temporary policies for federated users or assumed roles

### Best Practices
- **Principle of Least Privilege**: Grant minimum permissions required
- **Use Roles Instead of Long-term Access Keys**: For applications and services
- **Enable MFA**: For root account and privileged users
- **Regular Access Reviews**: Audit and rotate credentials periodically

## 🕵️ Detective Controls

### Monitoring & Logging
- **AWS CloudTrail**: Records API calls and account activity
- **AWS Config**: Tracks resource configurations and compliance over time
- **Amazon CloudWatch**: Monitors resources and applications
- **VPC Flow Logs**: Captures IP traffic going to and from network interfaces

### Threat Detection
- **Amazon GuardDuty**: Intelligent threat detection using ML and anomaly detection
- **AWS Security Hub**: Centralized view of security alerts and compliance status
- **Amazon Inspector**: Automated security assessments for EC2 instances and containers

## 🛡️ Infrastructure Protection

### Network Security
- **Security Groups**: Stateful virtual firewalls for EC2 instances
- **Network ACLs**: Stateless subnet-level traffic filtering
- **AWS WAF**: Web application firewall protecting against web exploits
- **AWS Shield**: DDoS protection service (Standard & Advanced)
- **AWS Network Firewall**: Managed network firewall service

### VPC Security
- **VPC Endpoints**: Private connectivity to AWS services without internet gateway
- **NAT Gateway**: Allows outbound internet access for private subnets
- **VPN & Direct Connect**: Secure hybrid cloud connectivity

## 🔒 Data Protection

### Encryption
- **Encryption at Rest**: 
  - **AWS KMS**: Managed encryption keys
  - **AWS CloudHSM**: Dedicated Hardware Security Modules
  - **Client-side Encryption**: Encrypt data before sending to AWS
- **Encryption in Transit**:
  - **TLS/SSL**: For web traffic and API calls
  - **AWS Certificate Manager**: Manage SSL/TLS certificates
  - **VPN/IPSec**: For secure network connections

### Key Management
- **AWS KMS Key Types**:
  - **AWS Managed Keys**: Automatic rotation, used by AWS services
  - **Customer Managed Keys (CMK)**: Full control over key policies and rotation
  - **Custom Key Stores**: Keys in CloudHSM for additional isolation

### Secrets Management
- **AWS Secrets Manager**: Rotate, manage, and retrieve secrets
- **AWS Systems Manager Parameter Store**: Store configuration data and secrets

## 🚨 Incident Response

### Preparation
- **AWS Config Rules**: Evaluate resource configurations against desired rules
- **AWS Systems Manager**: Automate operational tasks and patch management
- **Backup & Recovery**: Regular backups and disaster recovery plans

### Detection & Analysis
- **CloudWatch Alarms**: Notify when metrics breach thresholds
- **EventBridge**: Route security events to appropriate handlers
- **Lambda Functions**: Automated response to security events

### Containment & Recovery
- **Isolate Resources**: Use security groups and NACLs to contain threats
- **Snapshot & Restore**: Use EBS snapshots and AMIs for recovery
- **Forensic Analysis**: Preserve evidence using EBS snapshots and CloudTrail logs

## 📋 Compliance

### Compliance Programs
- **AWS Artifact**: Access AWS compliance reports and agreements
- **Well-Architected Framework**: Security pillar best practices
- **Industry Standards**: HIPAA, PCI DSS, SOC, ISO, FedRAMP

### Governance
- **AWS Organizations**: Centralized management of multiple accounts
- **Control Tower**: Set up and govern multi-account AWS environment
- **AWS Audit Manager**: Continuous auditing and evidence collection

## 🎯 Security Best Practices

### Account Management
- Use AWS Organizations for multi-account strategy
- Enable CloudTrail in all regions
- Use SCPs to enforce security policies across accounts

### Network Security
- Implement defense in depth with multiple security layers
- Use private subnets for sensitive resources
- Regularly review security groups and NACLs

### Data Protection
- Classify data based on sensitivity
- Enable encryption by default
- Implement proper key rotation policies

### Monitoring
- Set up comprehensive logging across all services
- Create alerts for suspicious activities
- Regular security assessments and penetration testing
