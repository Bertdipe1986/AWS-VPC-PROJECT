# AWS VPC Setup Project — KCVPC

## Overview
This project demonstrates how to design and deploy a Virtual Private Cloud (VPC) with both public and private subnets in **AWS EU-West-1 (Ireland)**. It includes routing, security groups, and network ACL configurations to ensure proper communication and security.

## Architecture Summary
- **VPC**: `KCVPC` — CIDR `10.0.0.0/16`
- **Subnets**:
  - `PublicSubnet`: CIDR `10.0.1.0/24` — internet-facing
  - `PrivateSubnet`: CIDR `10.0.2.0/24` — internal-only
- **Internet Gateway**: `KCIGW`
- **NAT Gateway**: In PublicSubnet for PrivateSubnet egress
- **Route Tables**:
  - PublicRouteTable → IGW
  - PrivateRouteTable → NAT Gateway
- **Security Groups**:
  - `PublicSG`: HTTP, HTTPS from anywhere; SSH from my IP
  - `PrivateSG`: PostgreSQL (5432) + SSH from PublicSG
- **NACLs**:
  - PublicNACL: allow web + SSH
  - PrivateNACL: allow from PublicSubnet
- **EC2 Instances**:
  - PublicEC2 (bastion/web server)
  - PrivateEC2 (database server)

---

## Purpose of Each Component

| Component           | Purpose |
|---------------------|---------|
| **VPC (`KCVPC`)**       | Provides isolated network space for AWS resources |
| **PublicSubnet**        | Hosts internet-facing resources like web servers or bastion hosts |
| **PrivateSubnet**       | Contains internal workloads such as databases, isolated from direct internet access |
| **Internet Gateway**    | Enables public subnet instances to connect to the internet |
| **NAT Gateway**         | Allows private subnet instances to initiate outbound connections to the internet without being exposed |
| **Route Tables**        | Defines how traffic is directed within the VPC |
| **Security Groups**     | Instance-level firewall controlling inbound/outbound traffic |
| **Network ACLs**        | Subnet-level firewall for additional security rules |
| **EC2 Instances**       | Virtual machines for running workloads and testing connectivity |

---

## Step-by-Step Process
1. **Create VPC**
2. **Create Public and Private Subnets**
3. **Attach Internet Gateway**
4. **Configure Public Route Table**
5. **Create NAT Gateway**
6. **Configure Private Route Table**
7. **Set Up Security Groups**
8. **Configure Network ACLs**
9. **Deploy EC2 Instances**
10. **Test Connectivity**
    - PublicEC2 accessible from internet
    - PrivateEC2 reachable via PublicEC2

---

## Diagram
![VPC Architecture](diagrams/vpc-architecture.png)

---

## Deliverables
- `docs/report.md` — detailed process with screenshots
- `diagrams/` — architecture diagram (Excalidraw export)
- `screenshots/` — console screenshots for each step
