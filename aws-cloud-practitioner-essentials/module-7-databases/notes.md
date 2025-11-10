# Module 7: Databases - Introduction & Shared Responsibility Model

## AWS Shared Responsibility Model for Databases

### Overview
The AWS shared responsibility model categorizes database services into three types based on administrative task ownership. Understanding these categories is crucial for the exam and real-world database management.

### Service Categories

## Fully Managed Database Services

### AWS Responsibilities (What AWS Handles)
- **Infrastructure Management**: Hardware provisioning, setup, and maintenance
- **Software Patching**: Automatic security updates and version upgrades
- **Backup Operations**: Automated backups and point-in-time recovery
- **Scaling**: Automatic scaling of storage and compute resources
- **High Availability**: Multi-AZ deployments and automatic failover
- **Performance Optimization**: Built-in performance monitoring and tuning
- **Security Patches**: Automatic application of security updates
- **Monitoring**: Built-in CloudWatch metrics and alerts
- **Disaster Recovery**: Built-in replication and recovery mechanisms

### Customer Responsibilities (What You Handle)
- **Database Design**: Table structures, indexes, and data models
- **Access Controls**: IAM policies, database users, and permissions
- **Data Security**: Encryption settings and data classification
- **Performance Tuning**: Query optimization and index management
- **Backup Configuration**: Retention policies and backup schedules
- **Monitoring Setup**: Custom alarms and performance thresholds

### Examples of Fully Managed Services
- **Amazon DynamoDB** (NoSQL)
- **Amazon Aurora** (Relational)
- **Amazon RDS** (Relational Database Service)
- **Amazon Redshift** (Data Warehouse)
- **Amazon DocumentDB** (Document Database)
- **Amazon Keyspaces** (Apache Cassandra compatible)

## Managed Database Services

### AWS Responsibilities
- **Hardware Provisioning**: Underlying server infrastructure
- **Basic Maintenance**: Routine backups and basic patching
- **Infrastructure Monitoring**: Hardware and network monitoring
- **Basic Security**: Infrastructure security and physical access

### Customer Responsibilities
- **Database Configuration**: Instance sizing and parameter groups
- **Performance Tuning**: Query optimization and index management
- **Advanced Backups**: Custom backup strategies and retention
- **Security Configuration**: Database-level security settings
- **High Availability Setup**: Configuring replication and failover
- **Software Updates**: Managing major version upgrades
- **Capacity Planning**: Monitoring and adjusting resources

### Key Characteristics
- More customer control over database engine
- Greater flexibility in configuration
- Increased operational responsibility
- Requires more database administration expertise

## Unmanaged Database Services

### AWS Responsibilities
- **Physical Infrastructure**: Data center security and power
- **Network Connectivity**: Basic network infrastructure
- **Hardware Maintenance**: Server hardware replacement

### Customer Responsibilities
- **Complete Database Management**: Installation, configuration, operation
- **Software Installation**: Database engine installation and setup
- **Security Management**: OS and database security hardening
- **Backup Strategy**: Designing and implementing backup solutions
- **High Availability**: Setting up replication and clustering
- **Performance Optimization**: All aspects of performance tuning
- **Disaster Recovery**: Complete DR strategy implementation
- **Patching and Updates**: All software updates and security patches

### Common Unmanaged Scenario
- **MySQL/PostgreSQL installed on EC2 instance**
- **MongoDB on EC2 instances**
- **Custom databases on self-managed servers**

## Comparison Table for Exam

| Responsibility Area | Fully Managed | Managed | Unmanaged |
|--------------------|---------------|---------|-----------|
| **Hardware Provisioning** | AWS | AWS | Customer |
| **Software Installation** | AWS | AWS | Customer |
| **Patching & Updates** | AWS | Shared | Customer |
| **Backups** | AWS | Shared | Customer |
| **Scaling** | AWS | Shared | Customer |
| **Performance Tuning** | Shared | Customer | Customer |
| **Security Configuration** | Shared | Customer | Customer |
| **High Availability** | AWS | Shared | Customer |

## Exam Critical Points

### Must Remember:
- **Fully Managed = Least Customer Responsibility**
- **Unmanaged = Most Customer Responsibility**
- **RDS is Managed, not Fully Managed** (important distinction)
- **DynamoDB is Fully Managed** (serverless, no servers to manage)

### Service Classification:
- **Fully Managed**: DynamoDB, Aurora Serverless, DocumentDB
- **Managed**: Amazon RDS, Amazon Redshift, Aurora Provisioned
- **Unmanaged**: Databases installed on EC2 instances

### Cost Implications:
- **Fully Managed**: Higher service cost, lower operational cost
- **Managed**: Balanced cost and control
- **Unmanaged**: Lower service cost, higher operational cost

## Real-World Scenarios

### When to Choose Fully Managed
- **Limited DBA Resources**: Small teams with minimal database expertise
- **Rapid Scaling Needs**: Applications with unpredictable growth
- **Compliance Requirements**: Need built-in security and compliance features
- **Cost Predictability**: Prefer operational expense over capital expense

### When to Choose Managed
- **Specific Requirements**: Need particular database versions or features
- **Existing Expertise**: Have experienced database administrators
- **Custom Configurations**: Require specific performance tuning
- **Cost Optimization**: Willing to manage some aspects to reduce costs

### When to Choose Unmanaged
- **Maximum Control**: Need complete control over database environment
- **Legacy Systems**: Migrating existing systems with custom configurations
- **Specialized Workloads**: Unique requirements not supported by managed services
- **Cost Sensitivity**: Willing to trade management overhead for lower costs

## Security Considerations

### Shared Security Model
- **AWS Secures the Cloud**: Infrastructure, hardware, software
- **You Secure in the Cloud**: Data, configuration, access controls

### Key Security Responsibilities
- **Data Encryption**: Configure encryption at rest and in transit
- **Access Management**: IAM policies and database user management
- **Network Security**: Security groups, NACLs, and VPC configuration
- **Audit Logging**: Enable and monitor database logs
- **Compliance**: Ensure data handling meets regulatory requirements

## Best Practices

### For Fully Managed Services
- Use IAM roles for database access when possible
- Enable automated backups and monitoring
- Use parameter groups for consistent configurations
- Implement multi-AZ deployments for production

### For Managed Services
- Regular performance monitoring and tuning
- Implement comprehensive backup strategies
- Use read replicas for read-heavy workloads
- Monitor and adjust instance sizes as needed

### For Unmanaged Services
- Implement automated backup and recovery procedures
- Use configuration management for consistency
- Regular security scanning and patching
- Comprehensive monitoring and alerting
