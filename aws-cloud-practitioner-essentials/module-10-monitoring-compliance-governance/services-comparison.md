# Monitoring, Compliance, and Governance – Service Comparisons

## Core Monitoring & Logging Services

| Service | Primary Function | Key Features | Use Cases |
|---------|------------------|--------------|-----------|
| **Amazon CloudWatch** | Monitoring and observability | – Metrics collection<br>- Logs management<br>- Alarms and actions<br>- Dashboards<br>- Events and automated responses | – Track CPU/memory usage<br>- Set scaling alarms<br>- Centralized log analysis<br>- Application performance monitoring |
| **AWS CloudTrail** | API activity logging | – Records all API calls (management and data events)<br>- Delivers log files to S3<br>- Integrated with CloudWatch Logs<br>- Supports organizational trails | – Security audits<br>- Compliance reporting<br>- Operational troubleshooting<br>- Change tracking |
| **AWS Config** | Resource configuration tracking | – Records configuration changes<br>- Evaluates against rules (compliance)<br>- Provides configuration history and relationships<br>- Automated remediation | – Compliance enforcement<br>- Security analysis<br>- Change management<br>- Inventory management |

### Comparison: CloudWatch vs CloudTrail vs Config

| Aspect | CloudWatch | CloudTrail | AWS Config |
|--------|------------|------------|------------|
| **Focus** | Performance & operational health | API activity & user actions | Resource configuration & compliance |
| **Data Type** | Metrics, logs, events | API call logs | Configuration items, relationships |
| **Retention** | Customizable (logs can expire) | 90 days by default (can store in S3 indefinitely) | Configuration history stored in S3 |
| **Alerting** | Yes (alarms) | Yes (via CloudWatch Logs) | Yes (via Config rules and SNS) |
| **Pricing** | Per metric, log ingestion, dashboard | Per event recorded | Per configuration item recorded, per rule evaluation |
| **Best For** | Real-time monitoring, scaling | Auditing, forensic analysis | Compliance, drift detection |

---

## Governance & Compliance Services

| Service | Primary Function | Key Features | Use Cases |
|---------|------------------|--------------|-----------|
| **AWS Organizations** | Multi-account management | – Centralized account creation<br>- Consolidated billing<br>- Service Control Policies (SCPs)<br>- API for automation | – Organize accounts by environment (dev, prod)<br>- Apply guardrails across all accounts<br>- Simplify billing |
| **AWS Trusted Advisor** | Best-practice recommendations | – Checks in 5 categories: cost, performance, security, fault tolerance, service limits<br>- Provides actionable guidance<br>- Core checks free; full checks with Business/Enterprise support | – Optimize costs<br>- Improve security posture<br>- Ensure service limits are not exceeded |
| **AWS Artifact** | Compliance reports access | – On-demand access to AWS compliance reports (SOC, PCI, ISO)<br>- Agreements (e.g., BAA, NDA)<br>- Centralized repository | – Fulfill audit requests<br>- Verify AWS compliance certifications |
| **AWS Audit Manager** | Continuous audit preparation | – Automates evidence collection<br>- Prebuilt frameworks (e.g., GDPR, HIPAA)<br>- Custom assessments<br>- Generates audit-ready reports | – Simplify audits<br>- Demonstrate compliance<br>- Reduce manual effort |
| **AWS License Manager** | Software license tracking | – Manage licenses from vendors (Microsoft, Oracle)<br>- Set license rules<br>- Track usage across accounts | – Avoid license overages<br>- Optimize license costs<br>- Ensure compliance with vendor terms |
| **AWS Service Catalog** | Approved service catalog | – Create and manage portfolios of approved products<br>- Enforce compliance via templates<br>- End‑user self‑service | – Standardize deployments<br>- Govern resource creation<br>- Enable teams while staying compliant |
| **AWS Well-Architected Tool** | Workload review | – Assess workloads against AWS best practices<br>- Provides recommendations<br>- Tracks improvements over time | – Improve architecture<br>- Ensure reliability and efficiency |

---

## Comparison: Organizations vs Trusted Advisor vs Artifact

| Aspect | AWS Organizations | AWS Trusted Advisor | AWS Artifact |
|--------|-------------------|---------------------|--------------|
| **Purpose** | Account governance | Optimization recommendations | Compliance documentation |
| **Scope** | All accounts in an organization | Individual account or organization | Global (AWS compliance) |
| **Key Feature** | SCPs to restrict actions | Best-practice checks | Downloadable reports |
| **User** | Central administrators | All users (basic), support tiers for full | Auditors, compliance officers |
| **Cost** | Free | Free core checks; full with support plan | Free |

---

## Integrated Workflow Example

1. **AWS Organizations** groups accounts (dev, test, prod) and applies SCPs.
2. **AWS CloudTrail** logs all API calls across accounts, stored centrally.
3. **AWS Config** continuously monitors resource configurations and flags non‑compliant resources.
4. **CloudWatch** collects metrics and logs, triggering alarms for anomalies.
5. **Trusted Advisor** provides cost and security recommendations.
6. **Audit Manager** collects evidence for compliance audits.
7. **Artifact** provides official compliance reports for auditors.

---

## Exam Tips

- **CloudWatch = Performance monitoring** (metrics, logs, alarms)
- **CloudTrail = API auditing** (who did what, when)
- **Config = Configuration tracking** (resource changes, compliance)
- **Organizations = Multi‑account management** with SCPs
- **Trusted Advisor = Best‑practice recommendations** (cost, security, etc.)
- **Artifact = Compliance reports download**
- **Audit Manager = Automate audit evidence collection**
- **License Manager = Track software licenses**

**Common Questions**:
- Which service helps track resource configuration changes? → **AWS Config**
- Which service provides a history of API calls? → **AWS CloudTrail**
- Which service monitors CPU utilization? → **CloudWatch**
- How to centrally manage multiple accounts? → **AWS Organizations**
- Where to download AWS compliance reports? → **AWS Artifact**
- Which service gives cost optimization recommendations? → **Trusted Advisor**

---

*Use these notes to understand the distinct roles and integrations of AWS monitoring, compliance, and governance services.*
