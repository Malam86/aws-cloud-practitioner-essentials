# Networking Services Comparison

## Security Groups vs NACLs
| Aspect | Security Groups | NACLs |
|--------|-----------------|-------|
| Level | Instance | Subnet |
| State | Stateful | Stateless |
| Rules | Allow only | Allow/Deny |

## Load Balancer Types
| Type | Layer | Use Case |
|------|-------|----------|
| ALB | 7 | Web apps |
| NLB | 4 | Performance |
| CLB | 4/7 | Legacy |
