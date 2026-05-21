# AWS Networking (VPC)

VPC (Virtual Private Cloud) provides an isolated network for AWS resources.

AWS networking concepts include:

- VPC
- Public Subnet
- Private Subnet
- Route Tables
- Security Groups

These concepts are fundamental for secure deployment architectures.

![alt text](image.png)

---

# VPC

A VPC is a private virtual network inside AWS.

Purpose:

- Resource isolation
- Traffic control
- Secure communication

---

# Public Subnet

Public subnet has internet access.

Usually contains:

- Load Balancer
- Bastion Host
- Public EC2 servers

---

# Private Subnet

Private subnet does not allow direct internet access.

Usually contains:

- Application servers
- RDS databases

---

# Route Tables

Route tables control traffic routing.

Example:

| Destination | Target |
|-------------|---------|
| 0.0.0.0/0 | Internet Gateway |

---

# Security Groups

Security Groups act as virtual firewalls.

Control:

- Inbound traffic
- Outbound traffic

Example:

Allow:

- SSH 22
- HTTP 80
- HTTPS 443

Restrict:

- Database ports from public internet.

---

# Production Networking Architecture

Internet

↓

Public Subnet

↓

Load Balancer

↓

Private Subnet

↓

EC2 Servers

↓

RDS Database

---

# Best Practices

Use:

✓ Private RDS

✓ Private application servers

✓ Restricted security groups

✓ Public access only for Load Balancer

Avoid:

✗ Public Database

✗ Open database ports

✗ Direct user access to backend servers
