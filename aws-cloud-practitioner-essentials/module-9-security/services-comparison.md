# Module 9: Security Services Comparison

## Identity & Access Management Services

### IAM vs AWS Organizations
| Feature | AWS IAM | AWS Organizations |
|---------|---------|-------------------|
| **Scope** | Single AWS account | Multiple AWS accounts |
| **Primary Use** | User/Role permissions management | Multi-account management & policies |
| **Policy Types** | Identity/Resource policies | Service Control Policies (SCPs) |
| **Granularity** | Fine-grained permissions | Account-level permissions boundaries |
| **Best For** | Managing access within an account | Managing security across multiple accounts |

### AWS SSO vs IAM Identity Center
| Feature | AWS SSO (Legacy) | IAM Identity Center (New) |
|---------|------------------|---------------------------|
| **Service Name** | AWS Single Sign-On | IAM Identity Center |
| **Integration** | Limited application integrations | Extensive pre-integrated applications |
| **Management** | Separate console | Integrated with IAM console |
| **Features** | Basic SSO capabilities | Advanced permission sets, multi-account access |
| **Recommendation** | Migrate to IAM Identity Center | Current recommended service |

## Network Security Services

### AWS WAF vs AWS Shield vs Network Firewall
| Service | Protection Level | Use Case | Cost |
|---------|------------------|----------|------|
| **AWS WAF** | Layer 7 (Application) | Protect web applications from common exploits | Pay-per-use |
| **AWS Shield Standard** | Layer 3/4 (Network) | Basic DDoS protection for all customers | Free |
| **AWS Shield Advanced** | Layer 3/4 & 7 | Enhanced DDoS protection with 24/7 support | Subscription + usage |
| **AWS Network Firewall** | Layer 3-7 | Stateful firewall with intrusion prevention | Pay-per-use |

### Security Groups vs NACLs
| Feature | Security Groups | Network ACLs |
|---------|-----------------|--------------|
| **Level** | Instance level | Subnet level |
| **State** | Stateful (return traffic allowed) | Stateless (return traffic must be explicit) |
| **Rule Evaluation** | All rules evaluated | Rules evaluated in order (lowest first) |
| **Allow/Deny** | Allow rules only | Allow and deny rules |
| **Use Case** | Primary instance protection | Additional subnet-level security |

## Encryption & Key Management

### AWS KMS vs AWS CloudHSM
| Feature | AWS KMS | AWS CloudHSM |
|---------|---------|--------------|
| **Management** | Fully managed by AWS | Customer-managed hardware |
| **Compliance** | FIPS 140-2 Level 2 | FIPS 140-2 Level 3 |
| **Key Control** | Shared with AWS | Exclusive customer control |
| **Integration** | Native with most AWS services | Requires custom integration |
| **Cost** | Pay per API call + monthly | Hourly fee per HSM instance |
| **Use Case** | General encryption needs | Regulatory requirements, dedicated HSM |

### Secrets Manager vs Systems Manager Parameter Store
| Feature | Secrets Manager | Parameter Store |
|---------|-----------------|-----------------|
| **Primary Use** | Database credentials, API keys | Configuration data, license codes |
| **Rotation** | Automatic secret rotation | Manual rotation only |
| **Cost** | Per secret per month | Free for standard, paid for advanced |
| **Size Limit** | 64KB | 4KB (standard), 8KB (advanced) |
| **Encryption** | KMS encryption required | Optional KMS encryption |
| **Best For** | Secrets requiring rotation | Configuration parameters, non-rotating secrets |

## Monitoring & Detective Controls

### CloudTrail vs AWS Config vs CloudWatch
| Service | What It Monitors | Primary Use | Retention |
|---------|------------------|-------------|-----------|
| **CloudTrail** | API calls and account activity | Security analysis, compliance auditing | 90 days (default), longer with S3 |
| **AWS Config** | Resource configurations over time | Compliance, change management, troubleshooting | Indefinite with S3 |
| **CloudWatch** | Resource performance and logs | Operational monitoring, alerting, troubleshooting | Customizable (logs, metrics) |

### GuardDuty vs Inspector vs Security Hub
| Service | Detection Type | Scope | Integration |
|---------|----------------|-------|-------------|
| **GuardDuty** | Threat intelligence, ML-based | Account-wide, VPC flow logs, CloudTrail | Security Hub, EventBridge |
| **Inspector** | Vulnerability assessment | EC2, ECR, Lambda functions | Security Hub, SNS |
| **Security Hub** | Security findings aggregation | Cross-account, multi-service | 40+ AWS and partner services |

## Compliance & Governance

### AWS Artifact vs Audit Manager vs Control Tower
| Service | Primary Function | Audience | Automation |
|---------|------------------|----------|------------|
| **AWS Artifact** | Compliance documentation access | Auditors, compliance teams | Manual access to reports |
| **Audit Manager** | Continuous evidence collection | Auditors, compliance teams | Automated evidence gathering |
| **Control Tower** | Multi-account governance setup | Cloud administrators, security teams | Automated guardrails, account setup |

## Data Protection Services

### Macie vs GuardDuty for Data Protection
| Feature | Amazon Macie | Amazon GuardDuty |
|---------|--------------|------------------|
| **Focus** | Data discovery and classification | Threat detection and monitoring |
| **Data Types** | PII, sensitive data in S3 | Network threats, compromised instances |
| **Method** | ML-based content analysis | Threat intelligence, anomaly detection |
| **Use Case** | Compliance (GDPR, HIPAA), data governance | Security monitoring, intrusion detection |

## Hybrid & Cross-Account Security

### AWS Directory Service Options
| Service | Use Case | Managed By | Integration |
|---------|----------|------------|-------------|
| **AD Connector** | Directory proxy to on-premises AD | Customer manages on-prem AD | Simple directory-enabled applications |
| **Managed Microsoft AD** | Full Active Directory in cloud | AWS manages AD infrastructure | Complex applications, Microsoft products |
| **Simple AD** | Basic directory capabilities | AWS manages simple directory | Linux workloads, basic user management |

## Cost & Implementation Considerations

### Free vs Paid Security Services
| Free Services | Paid Services | Consideration |
|---------------|---------------|---------------|
| IAM | GuardDuty | Start with free services, add paid based on risk |
| CloudTrail (management events) | CloudTrail (data events) | Enable data events only for critical resources |
| AWS Config (limited) | AWS Config (full) | Use Config rules selectively |
| Security Groups | WAF, Shield Advanced | Layer additional protection for public-facing resources |
| Basic KMS | CloudHSM | Use CloudHSM only for specific compliance needs |

## Service Integration Patterns

### Common Security Architecture Combinations

#### Multi-Account Security
