# Cloud Deployment

## What is Cloud Deployment?

Cloud deployment is the process of deploying applications, services, or infrastructure on cloud platforms instead of on-premises servers.

Applications are hosted on cloud providers such as:

- AWS
- Azure
- Google Cloud Platform (GCP)

---

# Why Cloud Deployment is Important

Cloud deployment provides:

- scalability
- high availability
- fault tolerance
- flexibility
- cost optimization
- global accessibility

---

# Traditional Deployment vs Cloud Deployment

| Traditional Deployment | Cloud Deployment |
|------------------------|-----------------|
| Physical servers | Virtual infrastructure |
| Manual scaling | Automatic scaling |
| High upfront cost | Pay-as-you-go |
| Limited flexibility | Highly flexible |
| Hardware maintenance required | Managed by cloud provider |

---

# Popular Cloud Providers

## Amazon Web Services (AWS)

Most widely used cloud platform.

Services:

- EC2
- S3
- RDS
- VPC
- EKS
- ECS

---

## Microsoft Azure

Popular in enterprise environments.

---

## Google Cloud Platform (GCP)

Strong in:

- Kubernetes
- machine learning
- data analytics

---

# Cloud Deployment Models

# 1. Public Cloud

Infrastructure shared across multiple organizations.

Examples:

- AWS
- Azure
- GCP

---

## Advantages

- low cost
- easy scalability
- fast setup

---

## Disadvantages

- less control
- shared environment

---

# 2. Private Cloud

Dedicated infrastructure for a single organization.

---

## Advantages

- higher security
- better control
- compliance support

---

## Disadvantages

- expensive
- maintenance responsibility

---

# 3. Hybrid Cloud

Combination of public and private cloud.

Example:

```text
Sensitive data → Private cloud
Web applications → Public cloud
```

---

## Advantages

- flexibility
- balanced security
- workload optimization

---

# Types of Cloud Services

# 1. IaaS (Infrastructure as a Service)

Provides infrastructure resources.

Examples:

- EC2
- Virtual Machines
- Storage
- Networking

---

## Responsibilities

Cloud provider manages:

- hardware
- virtualization

User manages:

- OS
- applications
- runtime

---

# 2. PaaS (Platform as a Service)

Provides application platform.

Examples:

- Heroku
- AWS Elastic Beanstalk

---

## Responsibilities

Cloud provider manages:

- infrastructure
- OS
- runtime

User manages:

- application code

---

# 3. SaaS (Software as a Service)

Complete software delivered through internet.

Examples:

- Gmail
- Slack
- Zoom

---

# Cloud Deployment Architecture

```text
Users
   ↓
DNS
   ↓
Load Balancer
   ↓
Application Servers
   ↓
Database
```

---

# Common Cloud Components

# Virtual Machines

Examples:

- AWS EC2
- Azure VM

Used for hosting applications.

---

# Storage

Examples:

- AWS S3
- EBS

Used for:

- backups
- files
- static websites

---

# Databases

Examples:

- RDS
- DynamoDB
- Cloud SQL

---

# Networking

Examples:

- VPC
- Subnets
- Route Tables
- Security Groups

---

# Containers

Examples:

- Docker
- Kubernetes

---

# Serverless

Examples:

- AWS Lambda
- Azure Functions

Runs code without managing servers.

---

# Common Cloud Deployment Methods

# 1. Virtual Machine Deployment

Application runs directly on virtual servers.

Example:

```text
Application → EC2 Instance
```

---

# 2. Container Deployment

Applications packaged into containers.

Example:

```text
Docker Container → Kubernetes Cluster
```

---

# 3. Serverless Deployment

Functions executed on demand.

Example:

```text
AWS Lambda Function
```

---

# Deployment Flow in Cloud

```text
Developer Pushes Code
          ↓
CI/CD Pipeline
          ↓
Build Application
          ↓
Run Tests
          ↓
Create Docker Image
          ↓
Push to Registry
          ↓
Deploy to Cloud
```

---

# High Availability in Cloud Deployment

High availability ensures applications remain accessible even during failures.

Achieved using:

- multiple servers
- multiple availability zones
- load balancers
- auto scaling

---

# Example Architecture

```text
Users
   ↓
Application Load Balancer
   ↓
EC2 Instances Across Multiple AZs
   ↓
RDS Database
```

---

# Auto Scaling

Automatically increases or decreases servers based on traffic.

Benefits:

- handles high traffic
- reduces cost
- improves availability

---

# Load Balancer

Distributes traffic across multiple servers.

Types:

- Application Load Balancer (ALB)
- Network Load Balancer (NLB)

---

# Containerized Cloud Deployment

Modern cloud-native applications commonly use:

- Docker
- Kubernetes

Advantages:

- portability
- scalability
- consistency

---

# Kubernetes Cloud Deployment

Kubernetes automates:

- deployment
- scaling
- container management
- self-healing

---

# Infrastructure as Code (IaC)

Infrastructure is created using code.

Tools:

- Terraform
- CloudFormation

Benefits:

- automation
- repeatability
- version control

---

# Cloud Security Best Practices

## Use IAM Roles

Avoid root account usage.

---

## Enable HTTPS

Encrypt network traffic.

---

## Store Secrets Securely

Use:

- AWS Secrets Manager
- Vault

---

## Use Private Subnets

Databases should remain private.

---

## Enable Monitoring

Use:

- CloudWatch
- Prometheus
- Grafana

---

# Common Cloud Deployment Tools

| Tool | Purpose |
|------|----------|
| Terraform | Infrastructure automation |
| Docker | Containerization |
| Kubernetes | Container orchestration |
| Jenkins | CI/CD |
| GitHub Actions | CI/CD |
| Ansible | Configuration management |

---

# Cloud Deployment Best Practices

## Automate Everything

Use CI/CD pipelines.

---

## Use Multiple Availability Zones

Improves fault tolerance.

---

## Monitor Applications

Track:

- CPU
- memory
- logs
- errors

---

## Use Backups

Always backup databases and storage.   

---

## Implement Security Properly

Use least privilege access.

---

# Common Challenges

## Downtime

Can occur during deployments.

---

## Cost Management

Cloud resources can become expensive.

---

## Security Risks

Improper configuration can expose systems.

---

## Scaling Problems

Applications may fail under heavy traffic.

---

# Real-World Example

Modern deployment flow:

```text
GitHub
   ↓
GitHub Actions
   ↓
Docker Build
   ↓
Push to ECR
   ↓
Deploy to Kubernetes
   ↓
Application Load Balancer
   ↓
Users
```

---

# Advantages of Cloud Deployment

- scalability
- flexibility
- faster deployment
- high availability
- disaster recovery
- global access
- automation support
