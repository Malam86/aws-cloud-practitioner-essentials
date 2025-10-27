# AWS Storage Services Comparison

## Performance Characteristics

| Service | Latency | Throughput | Use Case |
|---------|---------|------------|----------|
| **S3 Standard** | Milliseconds | High | Frequently accessed data |
| **EBS io2 Block Express** | Sub-millisecond | Very High | Mission-critical apps |
| **EFS Standard** | Low milliseconds | High | Shared file systems |
| **Glacier** | Hours | Medium | Archives |

## Cost Comparison

| Service | Cost per GB | Data Transfer | Best For |
|---------|-------------|---------------|----------|
| **S3 Standard** | $$ | $$ | General purpose |
| **S3 Glacier** | $ | $$$ (retrieval) | Archives |
| **EBS gp3** | $$ | $ | EC2 storage |
| **EFS** | $$$ | $ | Shared files |

## Durability & Availability

| Service | Durability | Availability | Data Protection |
|---------|------------|--------------|----------------|
| **S3** | 99.999999999% | 99.99% | Across multiple AZs |
| **EBS** | 99.8%-99.9% | 99.9% | Single AZ (snapshots cross-AZ) |
| **EFS** | 99.999999999% | 99.9% | Across multiple AZs |
| **Glacier** | 99.999999999% | 99.99% | Multiple geographic locations |
