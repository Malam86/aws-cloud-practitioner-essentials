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

# Module 7: Databases - Relational Database Services

## Relational Databases Overview

### What are Relational Databases?
- **Structured Data Storage**: Organize data into tables with rows and columns
- **Data Relationships**: Connect related data across multiple tables
- **SQL Language**: Use Structured Query Language for data management and queries
- **ACID Compliance**: Ensure data integrity with Atomicity, Consistency, Isolation, Durability

### Key Characteristics
- **Tables**: Data organized in rows (records) and columns (attributes)
- **Primary Keys**: Unique identifiers for each record
- **Foreign Keys**: Links between tables to establish relationships
- **Schema**: Pre-defined structure that enforces data types and relationships
- **Normalization**: Process of organizing data to reduce redundancy

### Real-World Example: Restaurant Inventory System
| ID | Product Name | Size | Price |
|----|-------------|------|-------|
| 1 | Medium roast ground coffee | 12 oz. | $13.95 |
| 2 | Single-origin whole bean coffee | 12 oz. | $21.95 |

**Benefits of This Structure:**
- Easy to query and analyze
- Consistent data format
- Scalable for growing inventory
- Maintains data integrity

## Amazon RDS (Relational Database Service)

### Overview
Amazon RDS is a **managed relational database service** that handles routine database administration tasks while maintaining high availability and security.

### Key Features

#### Managed Service Benefits
- **Automated Backups**: Point-in-time recovery and automated backup management
- **Software Patching**: Automatic security and feature updates
- **Hardware Provisioning**: AWS handles underlying infrastructure
- **Monitoring**: Built-in performance insights and CloudWatch integration

#### High Availability Features
- **Multi-AZ Deployments**: Automatic synchronous replication to standby instance in different Availability Zone
- **Automatic Failover**: Seamless failover during primary instance failure
- **Read Replicas**: Asynchronous copies for read-heavy workloads (up to 5 replicas)

#### Backup and Recovery
- **Automated Backups**: Daily backups with configurable retention (1-35 days)
- **DB Snapshots**: Manual, user-initiated backups that persist until deleted
- **Point-in-Time Recovery**: Restore to any second within backup retention period

#### Security Features
- **Network Isolation**: Deploy within Amazon VPC for network security
- **Encryption at Rest**: Data encrypted on storage volumes
- **Encryption in Transit**: SSL/TLS encryption for data moving to/from database
- **IAM Integration**: Manage access using AWS Identity and Access Management
- **Security Groups**: Firewall rules controlling database access

### Supported Database Engines

#### Open Source Options
- **MySQL**: Most popular open-source database
- **PostgreSQL**: Advanced open-source database with rich features
- **MariaDB**: MySQL-compatible community-driven database

#### Commercial Options
- **Oracle Database**: Enterprise-grade commercial database
- **Microsoft SQL Server**: Windows-based commercial database
- **Amazon Aurora**: AWS-optimized MySQL/PostgreSQL compatible database

### Scaling Capabilities

#### Vertical Scaling (Scale Up/Down)
- Change instance class (CPU, RAM, storage type)
- Can be done with minimal downtime (during maintenance window)
- **Use Case**: Sudden increase in workload, performance optimization

#### Horizontal Scaling (Read Replicas)
- Create up to 5 read replicas for read-heavy workloads
- Read replicas can be in different regions
- Can be promoted to standalone database if needed
- **Use Case**: Reporting, analytics, read scaling

### Use Cases

#### Web Applications
- Dynamic websites with user data
- Content management systems
- E-commerce platforms

#### Enterprise Workloads
- Customer relationship management (CRM)
- Enterprise resource planning (ERP)
- Business intelligence applications

#### E-commerce Platforms
- Product catalogs and inventory management
- Customer orders and transaction history
- User accounts and preferences

### Cost Optimization Strategies

#### Instance Right-Sizing
- Monitor CPU, memory, and storage usage
- Choose appropriate instance class (General Purpose, Memory Optimized, etc.)
- Use Performance Insights to identify bottlenecks

#### Storage Optimization
- General Purpose SSD (gp2/gp3): Balanced price and performance
- Provisioned IOPS SSD (io1/io2): High-performance workloads
- Magnetic storage: Legacy option (not recommended for new deployments)

#### Backup Cost Management
- Automated backups included in storage pricing
- DB Snapshots incur storage charges
- Consider lifecycle policies for snapshot management

## Amazon Aurora

### Overview
Amazon Aurora is a **MySQL and PostgreSQL-compatible** relational database built for the cloud, combining the performance and availability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases.

### Performance Features

#### High Performance Architecture
- **5x Performance**: Up to 5x better performance than standard MySQL
- **3x Performance**: Up to 3x better performance than standard PostgreSQL
- **Distributed Storage**: Data automatically spans multiple Availability Zones
- **Self-Healing Storage**: Automatically detects and repairs disk failures

#### Storage Architecture
- **Automated Scaling**: Storage automatically grows from 10GB to 128TB
- **Six-Way Replication**: Data copied across 3 Availability Zones (2 copies each)
- **Continuous Backup**: Backed up continuously to Amazon S3
- **Point-in-Time Recovery**: Granular recovery to specific moments

### High Availability Features

#### Multi-AZ Deployment
- **Automatic Failover**: Typically completes in less than 30 seconds
- **Read Replicas**: Up to 15 read replicas (vs 5 in RDS)
- **Global Database**: Cross-region replication for disaster recovery
- **Backtrack**: "Rewind" database to previous point in time without backups

#### Fault Tolerance
- **Storage-Level Replication**: Data replicated across multiple AZs
- **Instance-Level Redundancy**: Multiple database instances
- **Automatic Recovery**: Self-healing from instance and storage failures

### Aurora Serverless
- **Automatic Scaling**: Automatically starts, scales, and shuts down
- **Cost Effective**: Pay per second of database usage
- **No Capacity Planning**: Ideal for variable or unpredictable workloads
- **Use Cases**: Development, test, and variable production workloads

### Use Cases

#### Gaming Applications
- Player profiles and game state
- Leaderboards and achievements
- Real-time game analytics

#### Media and Content Management
- User-generated content storage
- Media metadata management
- Content delivery platforms

#### Real-Time Analytics
- Business intelligence dashboards
- Real-time reporting
- Operational analytics

### Benefits Comparison: RDS vs Aurora

| Feature | Amazon RDS | Amazon Aurora |
|---------|------------|---------------|
| **Performance** | Standard database performance | 5x MySQL, 3x PostgreSQL |
| **Storage Scaling** | Manual provisioning | Automatic (10GB to 128TB) |
| **Read Replicas** | Up to 5 | Up to 15 |
| **Replication** | Multi-AZ synchronous | Six-way replication across AZs |
| **Backup** | Automated + manual snapshots | Continuous to S3 |
| **Cost** | Lower for small workloads | Better value at scale |
| **Failover Time** | 60-120 seconds | Typically under 30 seconds |

## Exam Critical Points

### Must Remember:
- **RDS is Managed**: AWS handles infrastructure, you manage database
- **Aurora is High-Performance**: Built for cloud with better performance
- **Multi-AZ vs Read Replicas**: Multi-AZ for HA, Read Replicas for scaling
- **Backup Types**: Automated (point-in-time) vs Manual (snapshots)

### Service Selection Guide:
- **Choose RDS When**:
  - Standard database requirements
  - Cost-sensitive projects
  - Specific database engine features needed
  - Predictable workloads

- **Choose Aurora When**:
  - High-performance requirements
  - Enterprise applications
  - Need high availability and durability
  - Cost-effective at scale

### Security Best Practices:
- Always enable encryption at rest
- Use IAM database authentication when possible
- Deploy in private subnets within VPC
- Use security groups to restrict access
- Enable automated backups and monitoring
