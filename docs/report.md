# KCVPC AWS VPC Setup Report

## Purpose
Secure, scalable AWS VPC with segregated public/private resources.

## Components & Functions
| Component           | Purpose |
|---------------------|---------|
| VPC (`KCVPC`)       | Isolated network space |
| PublicSubnet        | Internet-facing resources |
| PrivateSubnet       | Internal-only workloads |
| Internet Gateway    | Outbound/Inbound for public subnet |
| NAT Gateway         | Outbound for private subnet |
| Route Tables        | Direct traffic flows |
| Security Groups     | Instance-level firewall |
| Network ACLs        | Subnet-level firewall |
| EC2 Instances       | Test and host workloads |

## Step-by-Step Screenshots
(Add images here from `/screenshots`)

## Diagram
(Attach from `/diagrams/vpc-architecture.png`)

---
