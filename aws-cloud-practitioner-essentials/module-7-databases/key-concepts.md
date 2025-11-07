# Database Key Concepts

## Database Types

### Relational Databases (SQL)
- **Structured Data**: Organized in tables with rows and columns
- **ACID Compliance**: 
  - **Atomicity**: All operations in transaction succeed or all fail
  - **Consistency**: Database remains consistent before and after transaction
  - **Isolation**: Concurrent transactions don't interfere
  - **Durability**: Committed transactions persist despite failures
- **Fixed Schema**: Pre-defined structure with relationships
- **SQL Language**: Standardized query language
- **Vertical Scaling**: Typically scale by increasing server capacity

### Non-Relational Databases (NoSQL)
- **Flexible Schema**: Dynamic structure, no fixed schema required
- **Unstructured Data**: Handles various data types (documents, key-value, graphs)
- **BASE Properties**:
  - **Basically Available**: System seems to work all the time
  - **Soft State**: State may change over time
  - **Eventual Consistency**: Becomes consistent over time
- **Horizontal Scaling**: Scale by adding more servers
- **Varied Data Models**: Document, key-value, graph, column-family

## Core Database Concepts

### Database Scaling

#### Vertical Scaling (Scale Up)
- Increase capacity of existing server (more CPU, RAM, storage)
- **Pros**: Simple to implement, consistent performance
- **Cons**: Hardware limits, single point of failure, expensive
- **Use Case**: Traditional relational databases

#### Horizontal Scaling (Scale Out)
- Add more servers to distribute load
- **Pros**: Virtually unlimited scale, fault tolerance, cost-effective
- **Cons**: More complex, potential consistency issues
- **Use Case**: NoSQL databases, big data applications

### Database Replication

#### Synchronous Replication
- Data written to multiple locations simultaneously
- **Pros**: Strong consistency, no data loss
- **Cons**: Higher latency, dependent on slowest node
- **Use Case**: Financial systems, critical transactions

#### Asynchronous Replication
- Data written to primary first, then replicated
- **Pros**: Lower latency, better performance
- **Cons**: Potential data loss, eventual consistency
- **Use Case**: Read replicas, disaster recovery

### Consistency Models

#### Strong Consistency
- All reads return most recent write
- **Use Case**: Banking systems, inventory management

#### Eventual Consistency
- Reads may temporarily show old data, but eventually consistent
- **Use Case**: Social media, content delivery

#### Read-After-Write Consistency
- Reads immediately after write see the written data
- **Use Case**: User sessions, recent activity

## AWS Database Architecture Patterns

### Multi-AZ Deployments
- Automatic synchronous replication to standby in different AZ
- Automatic failover during primary failure
- **Use Case**: High availability requirements

### Read Replicas
- Asynchronous copies for read-heavy workloads
- Can be promoted to standalone database
- **Use Case**: Reporting, analytics, read scaling

### Global Databases
- Cross-region replication for disaster recovery
- Low-latency access worldwide
- **Use Case**: Global applications, disaster recovery

## Performance Concepts

### IOPS (Input/Output Operations Per Second)
- Measure of storage performance
- Critical for database throughput
- **Provisioned IOPS**: Guaranteed performance level
- **General Purpose**: Baseline performance with bursting

### Throughput
- Amount of data transferred per second
- Measured in MB/s or GB/s
- Key for data-intensive operations

### Latency
- Time taken for database operations
- Critical for user experience
- Affected by network, storage, and database design

## Security Concepts

### Encryption
- **At Rest**: Data encrypted on disk
- **In Transit**: Data encrypted during network transfer
- **Key Management**: AWS KMS for encryption keys

### Network Isolation
- **VPC**: Virtual Private Cloud for network isolation
- **Security Groups**: Firewall for EC2 instances
- **Subnets**: Network segmentation within VPC

### Access Control
- **IAM Policies**: Identity and Access Management
- **Database Authentication**: Native database users vs IAM
- **Parameter Groups**: Database configuration settings

## Backup and Recovery

### Automated Backups
- Point-in-time recovery capability
- Configurable retention periods
- Storage in Amazon S3

### Snapshots
- Manual backups triggered by user
- Stored until explicitly deleted
- Used for long-term retention

### Recovery Time Objective (RTO)
- Maximum acceptable time to restore service
- Drives backup strategy and infrastructure

### Recovery Point Objective (RPO)
- Maximum acceptable data loss measured in time
- Drives replication and backup frequency
