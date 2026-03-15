# Monitoring, Compliance, and Governance – Key Concepts

## Monitoring Concepts

### What is Monitoring?
- **Continuous observation** of systems, applications, and infrastructure
- **Purpose**: Ensure performance, availability, and security
- **Data collected**: Metrics, logs, events, traces

### Key Monitoring Components

#### Metrics
- **Definition**: Numerical data points tracked over time (e.g., CPU utilization, network traffic)
- **Use**: Measure performance, detect anomalies, trigger alarms

#### Logs
- **Definition**: Detailed records of events, errors, transactions
- **Use**: Troubleshooting, security analysis, audit trails

#### Alarms
- **Definition**: Threshold-based notifications triggered when metrics cross defined limits
- **Use**: Proactive response to issues (e.g., scale up when CPU > 80%)

#### Dashboards
- **Definition**: Visual displays of metrics and logs for real-time insights
- **Use**: Centralized view of system health

### AWS Monitoring Services
- **Amazon CloudWatch**: Collects and visualizes metrics, logs, and events; sets alarms; automates responses
- **AWS CloudTrail**: Records API activity for auditing and governance
- **AWS Config**: Tracks resource configuration changes and compliance

---

## Logging and Auditing Concepts

### What is Logging?
- **Recording events** that happen in an AWS environment
- **Types**: API calls, resource changes, access logs

### What is Auditing?
- **Reviewing logs and configurations** to verify compliance and detect security issues
- **Purpose**: Meet regulatory requirements, internal policies

### AWS Logging and Auditing Services
- **AWS CloudTrail**: Provides a history of AWS API calls for governance, compliance, and operational auditing
- **AWS Config**: Continuously monitors and records resource configurations and evaluates against desired policies

---

## Compliance Concepts

### What is Compliance?
- **Adhering to laws, regulations, standards, and best practices** (e.g., GDPR, HIPAA, PCI DSS)
- **Shared Responsibility**: AWS provides compliant infrastructure; customers must configure services to meet standards

### AWS Compliance Resources
- **AWS Artifact**: Self-service portal for on-demand access to AWS compliance reports and agreements
- **AWS Audit Manager**: Helps continuously audit AWS usage to assess risk and compliance
- **AWS Compliance Center**: Central hub for compliance information and whitepapers

---

## Governance Concepts

### What is Governance?
- **Framework of policies and controls** to manage AWS resources efficiently, securely, and cost-effectively
- **Key aspects**: Access control, cost management, resource organization, compliance enforcement

### AWS Governance Tools

#### AWS Organizations
- **Central management** of multiple AWS accounts
- **Features**:
  - Consolidated billing
  - Policy-based management (Service Control Policies – SCPs)
  - Account creation and grouping

#### AWS Service Catalog
- **Create and manage** catalogs of approved IT services
- **Enforce compliance** by restricting users to pre‑approved configurations

#### AWS License Manager
- **Track and manage** software licenses (e.g., Microsoft, Oracle) across AWS and on-premises
- **Prevent license violations** and optimize costs

#### AWS Trusted Advisor
- **Automated best-practice checks** across five categories:
  - Cost optimization
  - Performance
  - Security
  - Fault tolerance
  - Service limits
- **Provides recommendations** to improve your environment

---

## Additional Key Terms

### Service Control Policies (SCPs)
- **Centrally manage permissions** across accounts in an AWS Organization
- **Define maximum permissions** for member accounts

### AWS Well-Architected Tool
- **Review and improve** workloads based on the AWS Well-Architected Framework
- **Covers pillars**: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization

### AWS Systems Manager
- **Centralized operations** service for managing resources at scale
- **Includes**: Inventory, patch management, session manager, automation

### AWS Config Rules
- **Custom or managed rules** to evaluate resource configurations against desired policies
- **Remediation actions** can be automated

---

## Summary Table of Key Concepts

| Concept | Description | AWS Service |
|---------|-------------|-------------|
| Monitoring | Collect and visualize performance data | CloudWatch |
| Logging | Record API calls and events | CloudTrail |
| Auditing | Review logs and configurations | CloudTrail, Config |
| Compliance | Adhere to regulatory standards | Artifact, Audit Manager |
| Governance | Manage accounts, policies, costs | Organizations, Trusted Advisor |
| License Management | Track software licenses | License Manager |
| Best Practice Checks | Automated recommendations | Trusted Advisor |
