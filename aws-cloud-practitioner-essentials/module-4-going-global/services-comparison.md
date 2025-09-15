# Global Services Comparison

## CloudFront vs Traditional Hosting

| Aspect | Traditional Hosting | CloudFront + S3 |
|--------|---------------------|-----------------|
| **Global Latency** | High (single location) | Low (edge locations) |
| **Scalability** | Limited by server | Virtually unlimited |
| **Cost** | Fixed server costs | Pay-per-request |
| **Management** | Server maintenance | Fully managed |

## Route 53 Routing Policies

| Policy | Use Case | Example |
|--------|----------|---------|
| **Simple** | Single resource | example.com → 1.2.3.4 |
| **Weighted** | A/B testing | 70% A, 30% B |
| **Latency** | Performance | Lowest latency region |
| **Geolocation** | Local content | Country-specific sites |
| **Failover** | Disaster recovery | Primary/backup |

## Region Selection Factors

| Factor | Consideration |
|--------|--------------|
| **Latency** | Proximity to users |
| **Cost** | Regional pricing differences |
| **Compliance** | Data sovereignty laws |
| **Service Availability** | Not all services in all regions |
| **Disaster Recovery** | Geographic separation |
