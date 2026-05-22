# Deployment Documentation

# 1. What is Deployment

Deployment is the process of making an application, software system, or service available for users to access and use.

In simple words:

> Deployment means moving software from a development environment to a live environment (production).

After developers build an application, it must be delivered to a server or infrastructure where end users can access it.

---

## Simple Deployment Flow

```text
Developer Code
      ↓
Build Application
      ↓
Testing
      ↓
Deployment Pipeline
      ↓
Production Server
      ↓
End Users
```

---

## Example

A developer creates a FastAPI application locally.

Local environment:

```text
Laptop → Development
```

Deployment:

```text
Local Machine
    ↓
AWS EC2 Server
    ↓
Nginx
    ↓
Public Users
```

The application is now accessible over the internet.

---

## Business Importance

Deployment helps companies:

- Deliver new features
- Fix production bugs
- Release updates
- Scale applications
- Improve customer experience
- Maintain system reliability

---

## Example

A banking company launches a payment update.

Without deployment:

```text
Code exists but users cannot access it.
```

With deployment:

```text
New feature available to millions of customers.
```

---

# 3. Deployment Lifecycle

Modern software deployment follows a lifecycle.

```text
Code Development
      ↓
Build
      ↓
Testing
      ↓
Packaging
      ↓
Deployment
      ↓
Monitoring
      ↓
Maintenance
```

---

## Step 1 — Development

Developers write source code.

Examples:

- Java
- Python
- Node.js
- Go
- .NET

---

## Step 2 — Build

Application artifacts are created.

Examples:

Java:

```text
JAR / WAR
```

Python:

```text
Docker Image
Wheel Package
```

Node.js:

```text
Production Build
```

---

## Step 3 — Testing

Applications are validated.

Common tests:

- Unit Testing
- Integration Testing
- Performance Testing
- Security Testing

---

## Step 4 — Deployment

Application is released to infrastructure.

Examples:

- EC2
- Kubernetes
- Docker Containers
- Bare Metal Servers
- Serverless Platforms

---

## Step 5 — Monitoring

Production systems are observed.

Tools:

- Prometheus
- Grafana
- CloudWatch
- ELK Stack

---

# 4. Types of Deployment

Deployment can be categorized based on infrastructure and process.

---

## 4.1 Manual Deployment

Deployment performed manually by engineers.

Example:

```bash
git pull
npm install
systemctl restart nginx
```

---

### Characteristics

- Human controlled
- Slow process
- Error-prone

---

### Used In

Usually:

- Small projects
- Learning environments
- Legacy systems

---

## 4.2 Automated Deployment

Deployment performed automatically using tools.

Example:

```text
GitHub Push
    ↓
CI/CD Pipeline
    ↓
Production Deployment
```

---

### Tools

- Jenkins
- GitHub Actions
- GitLab CI/CD
- CircleCI

---

### Benefits

- Faster releases
- Reduced human errors
- Better consistency

---

## 4.3 Continuous Delivery

Code is automatically prepared for release.

Human approval is required.

Flow:

```text
Code Commit
     ↓
Testing
     ↓
Build
     ↓
Ready for Production
     ↓
Manual Approval
```

---

## 4.4 Continuous Deployment

Every validated change automatically reaches production.

No manual approval.

Flow:

```text
Code Push
    ↓
Pipeline
    ↓
Production Release
```

---

Companies using this:

- Netflix
- Amazon
- Facebook

---

## 4.5 On-Premises Deployment

Application deployed inside company infrastructure.

Example:

```text
Company Data Center
```

---

### Used By

Common in:

- Banks
- Government
- Healthcare

---

## 4.6 Cloud Deployment

Application deployed on cloud providers.

Examples:

- AWS
- Azure
- GCP

---

### Advantages

- Scalability
- High availability
- Reduced infrastructure management

---

## 4.7 Hybrid Deployment

Combination of cloud and on-premises systems.

Example:

```text
Cloud Servers + Local Data Center
```

---

Used in enterprises requiring partial cloud adoption.

---

# 5. Most Used Deployment Techniques in Present Companies

Modern companies use advanced deployment strategies to reduce downtime and risk.

---

# 5.1 Recreate Deployment

## What is Recreate Deployment?

Recreate Deployment is the **simplest deployment strategy**.

In this approach:

1. Stop the currently running application.
2. Remove the old application version.
3. Deploy the new version.
4. Start the application again.

Only **one version exists at a time**.

---

## Deployment Flow

```text
Running Version
      ↓
Stop Old Version
      ↓
Remove Old Application
      ↓
Deploy New Version
      ↓
Start New Version
```

---

## Example

Suppose an application currently runs:

```text
Version 1 (Production)
```

Deployment Process:

```text
Version 1 → STOPPED
      ↓
Deploy Version 2
      ↓
Version 2 → STARTED
```

---

### Real World Scenario — One Line Explanation

A company running a Spring Boot application on a single Linux server stops the old application version, removes the existing build, deploys the new build, and starts the new version, causing temporary downtime during the deployment process.

## Advantages

### Simple Implementation

Easy to understand and configure.

---

### Low Infrastructure Cost

Requires only one environment.

---

### Low Operational Complexity

No traffic routing or multiple environments.

---

## Disadvantages

### Downtime Occurs

Application becomes unavailable during deployment.

---

### Higher Deployment Risk

If deployment fails:

```text
Application may remain offline.
```

---

## Commonly Used In

- Small applications
- Internal company tools
- Development environments
- Non-critical systems

---


# 5.2 Rolling Deployment

## What is Rolling Deployment?

Rolling Deployment updates application servers **gradually**.

Instead of updating everything at once, servers are updated **in batches**.

Old and new versions temporarily coexist.

---

## Deployment Flow

```text
Server1 → Update
Server2 → Update
Wait Validation
Server3 → Update
Server4 → Update
Continue...
```

---

## Example

Company Infrastructure:

```text
10 Application Servers
```

Deployment Strategy:

Update:

```text
2 servers at a time
```

Before Deployment:

```text
Server1 → v1
Server2 → v1
Server3 → v1
Server4 → v1
```

Step 1:

```text
Server1 → v2
Server2 → v2
Server3 → v1
Server4 → v1
```

Final:

```text
All Servers → v2
```

---

## Traffic Flow

Requests are managed through a Load Balancer.

```text
Users
   ↓
Load Balancer
   ↓
Server1 → v2
Server2 → v1
Server3 → v1
```

Some users access the new version.

Others continue using the old version.

---

## Advantages

### Minimal Downtime

Application remains online.

---

### Controlled Rollout

Problems detected early.

---

## Disadvantages

### Mixed Versions Exist

Temporary coexistence of:

```text
Version1 + Version2
```

---

### Compatibility Issues Possible

Example:

New version requires:

```text
user_phone column
```

Old version may not support it.

---

### Rollback Complexity

Rollback must also happen gradually.

---

# 5.3 Blue-Green Deployment

## What is Blue-Green Deployment?

Blue-Green Deployment uses **two identical production environments**.

One environment handles live traffic.

The second environment hosts the new release.

---

## Environment Structure

### Blue Environment

Current production.

Live traffic served here.

### Green Environment

New deployment environment.

Used for validation and testing.

---

## Deployment Flow

```text
Blue Production
      ↓
Deploy to Green
      ↓
Testing & Validation
      ↓
Traffic Switch
      ↓
Green Becomes Production
```

---

## Architecture Example

Before Deployment:

```text
Users
   ↓
Load Balancer
   ↓
BLUE → Version1
GREEN → Idle
```

Deploy New Release:

```text
Deploy Version2 → GREEN
```

After Validation:

```text
Switch Traffic → GREEN
```

---

## Rollback Process

If deployment fails:

```text
Switch Traffic Back → BLUE
```

Rollback happens quickly.

---

## Advantages

### Near-Zero Downtime

No production interruption.

---

### Fast Rollback

Traffic switching is immediate.

---

### Safe Validation

Testing completed before exposure.

---

## Disadvantages

### Higher Infrastructure Cost

Requires:

- Double servers
- Double storage
- Duplicate environments

---

### Configuration Complexity

Both environments must remain synchronized.

---

## Commonly Used In

- Banking Applications
- Enterprise SaaS
- E-Commerce Platforms
- Healthcare Systems

---

# 5.4 Canary Deployment

## What is Canary Deployment?

Canary Deployment releases the new version to a **small percentage of users first**.

Instead of deploying to everyone immediately.

---

## Deployment Flow

Initial Release:

```text
95% Users → Old Version
5% Users → New Version
```

Monitoring Phase:

Observe:

- Errors
- CPU usage
- Performance
- Crashes

If healthy:

```text
25% → New Version
50% → New Version
100% → New Version
```

---

## Traffic Flow

```text
Users
    ↓
Load Balancer
    ↓
95% → Version1
5% → Version2
```

---

## Advantages

### Low Deployment Risk

Limited exposure.

Only a small user group is affected.

---

### Real Production Testing

Actual customer behavior is observed.

---

### Early Failure Detection

Problems found before full rollout.

---

## Disadvantages

### Requires Advanced Monitoring

Monitoring tools needed:

- Prometheus
- Grafana
- CloudWatch

---

### Complex Traffic Routing

Load balancer configuration required.

---

## Commonly Used By

- Netflix
- Google
- Amazon
- Facebook

---

# 5.5 A/B Deployment

## What is A/B Deployment?

A/B Deployment delivers **different application versions to different user groups**.

Purpose:

Measure:

- User behavior
- Conversion rates
- Performance
- Feature effectiveness

---

## Deployment Flow

```text
Group A → Version A
Group B → Version B
```

---

## Example

E-commerce Checkout Experiment.

Version A:

```text
Blue Purchase Button
```

Version B:

```text
Green Purchase Button
```

Measured Metrics:

- Click Rate
- Conversion Rate
- Purchase Completion

---

## Example Metrics Table

| Metric | Version A | Version B |
|----------|-----------|-----------|
| Click Rate | 20% | 31% |
| Conversion | 8% | 12% |

Result:

Version B performs better.

---

## Advantages

### Data Driven Decisions

Real user behavior drives decisions.

---

### Product Optimization

Improve KPIs and business metrics.

---

### Feature Validation

Validate new ideas safely.

---

## Disadvantages

### Analytics Complexity

Detailed tracking required.

---

### User Routing Complexity

User segmentation required.

---

## Commonly Used In

- Marketing Platforms
- Recommendation Engines
- UI Experiments
- Product Optimization

---

## Companies Using A/B Testing

- Amazon
- Netflix
- Booking.com
- Meta

---

# 5.6 Shadow Deployment

## What is Shadow Deployment?

Shadow Deployment runs the new version **silently in parallel**.

Users continue interacting with the old system.

Production traffic is copied to the new environment.

---

## Deployment Flow

```text
Production Traffic
        ↓
Old Version
        ↓
Traffic Copy
        ↓
Shadow Environment
```

Users only see responses from the old version.

---

## Architecture Example

```text
Users
   ↓
Load Balancer
   ↓
Production Version
         ↓
Traffic Mirroring
         ↓
Shadow Version
```

---

## Example

Production Environment:

```text
Version1
```

Shadow Environment:

```text
Version2
```

Incoming Requests:

```text
/login
/payment
/cart
```

Requests copied to both systems.

Only Version1 responses reach users.

---

## Advantages

### Safe Validation

Users are unaffected.

---

### Real Traffic Testing

Uses actual production traffic.

---

### Performance Verification

Useful for:

- Load testing
- CPU benchmarking
- Memory analysis

---

## Disadvantages

### High Resource Cost

Two environments required.

---

### Higher Operational Complexity

Traffic mirroring setup required.

---

### Data Synchronization Challenges

Avoid duplicate operations.

Example:

Do not execute duplicate payments.

---

## Commonly Used In

- Enterprise Platforms
- Financial Systems
- Large APIs
- Cloud Providers

---

# 6. CI/CD and Deployment

Modern deployment heavily depends on CI/CD.

---

## CI — Continuous Integration

Developers frequently merge code.

Pipeline automatically:

- Builds
- Tests
- Validates

---

## CD — Continuous Delivery / Deployment

Automates release process.

---

Flow:

```text
Developer Commit
       ↓
CI Pipeline
       ↓
Testing
       ↓
Artifact Build
       ↓
Deployment
       ↓
Production
```

---

### Popular CI/CD Tools

| Tool | Usage |
|------|------|
| Jenkins | Enterprise CI/CD |
| GitHub Actions | GitHub automation |
| GitLab CI/CD | Integrated pipelines |
| ArgoCD | Kubernetes GitOps |
| AWS CodePipeline | AWS deployments |

---

# 7. Real-World Deployment Practices

Present companies commonly use:

```text
Docker
     ↓
Kubernetes
     ↓
CI/CD Pipeline
     ↓
Cloud Infrastructure
```

---

Typical enterprise architecture:

```text
Developer
    ↓
Git Repository
    ↓
CI/CD Pipeline
    ↓
Docker Build
    ↓
Kubernetes Cluster
    ↓
Production
```

---

Most companies prefer:

- Containerization
- Infrastructure as Code
- Automated deployment
- Observability
- Zero-downtime releases

---

# 8. Advantages and Disadvantages of Deployment Techniques

| Technique | Advantages | Disadvantages |
|------------|------------|---------------|
| Recreate | Simple | Downtime |
| Rolling | Minimal downtime | Version inconsistency |
| Blue-Green | Fast rollback | Higher cost |
| Canary | Reduced risk | Complex setup |
| A/B | Business experimentation | Management overhead |
| Shadow | Safe validation | High resource consumption |

---

## 9. Best Practices in Modern Deployment

Modern companies follow deployment best practices to achieve:

- Faster releases
- Reliable deployments
- High availability
- Security
- Scalability
- Automation

These practices are widely used in **DevOps**, **Cloud Engineering**, and **Production Environments**.

---

# 9.1 Infrastructure as Code (IaC)

## What is Infrastructure as Code?

Infrastructure as Code (IaC) is the practice of **managing infrastructure using code instead of manual setup**.

Instead of manually creating servers, networks, or databases from a cloud console, engineers define infrastructure using configuration files.

---

## Traditional Infrastructure Management

Without IaC:

Engineers manually create:

- Servers
- Databases
- Load Balancers
- Networks
- Security Groups

Problems:

- Human errors
- Inconsistent environments
- Slow provisioning
- Difficult replication

---

## Infrastructure as Code Approach

Infrastructure is defined using code.

Example:

```text
Server Configuration
Network Configuration
Database Configuration
Security Configuration
```

Everything becomes version-controlled.

---

## Benefits of IaC

### Automation

Infrastructure creation becomes automatic.

---

### Consistency

Development, staging, and production environments remain identical.

---

### Repeatability

Same infrastructure can be recreated anytime.

---

### Version Control

Infrastructure changes tracked through Git.

---

## Popular IaC Tools

### Terraform

Multi-cloud Infrastructure as Code tool.

Supports:

- AWS
- Azure
- Google Cloud
- Kubernetes

Example:

```text
Terraform Code
      ↓
terraform apply
      ↓
AWS Resources Created
```

---

### CloudFormation

AWS-native Infrastructure as Code service.

Used to provision:

- EC2
- VPC
- IAM
- RDS
- S3

Example:

```text
CloudFormation Template
        ↓
AWS Stack Creation
```

---

## Real World Example

Company deployment setup:

```text
Terraform Code
      ↓
Creates VPC
Creates Subnets
Creates EC2
Creates RDS
Creates Security Groups
```

Entire infrastructure is deployed automatically.

---

# 9.2 Containerization

## What is Containerization?

Containerization packages an application together with:

- Source code
- Runtime
- Dependencies
- Libraries
- System configuration

into a portable container.

---

## Why Containerization is Needed

Traditional deployment problems:

```text
Works on my machine.
Fails in production.
```

Different environments may contain:

- Different libraries
- Different runtimes
- Different operating systems

Containerization solves this problem.

---

## Containerization Workflow

```text
Application Code
       ↓
Docker Build
       ↓
Container Image
       ↓
Deploy Anywhere
```

---

## Benefits

### Portability

Same application runs everywhere.

---

### Environment Consistency

Development and production environments match.

---

### Fast Deployment

Containers start quickly.

---

## Popular Containerization Tools

### Docker

Most widely used container platform.

Used for:

- Building images
- Running containers
- Shipping applications

Example:

```text
Dockerfile
      ↓
Docker Image
      ↓
Docker Container
```

---

### Podman

Container platform alternative.

Advantages:

- Daemonless architecture
- Improved security model

---

## Real World Example

Company Application:

Spring Boot Service.

Container Packaging:

```text
Spring Boot App
       ↓
Docker Image Creation
       ↓
Push to Registry
       ↓
Deploy to Kubernetes
```

---

# 9.3 Orchestration

## What is Orchestration?

Orchestration automates the management of multiple containers.

When organizations run hundreds or thousands of containers, manual management becomes impossible.

Orchestration platforms manage:

- Deployment
- Scaling
- Recovery
- Networking
- Service discovery

---

## Why Orchestration is Important

Without orchestration:

Teams manually handle:

- Container startup
- Failures
- Scaling
- Traffic routing

This becomes difficult at large scale.

---

## Orchestration Workflow

```text
Containers
     ↓
Orchestration Platform
     ↓
Deployment Management
Scaling
Self-Healing
Networking
```

---

## Major Orchestration Tools

### Kubernetes

Industry-standard container orchestration platform.

Capabilities:

- Auto Scaling
- Self Healing
- Rolling Updates
- Service Discovery
- Load Balancing

Example:

```text
Deploy Application
       ↓
Kubernetes Cluster
       ↓
Pods Created
```

If a pod crashes:

```text
Kubernetes Automatically Recreates It
```

---

### ECS (Elastic Container Service)

AWS managed container orchestration service.

Integrates with:

- EC2
- IAM
- CloudWatch

---

### Nomad

Lightweight orchestration tool by HashiCorp.

Supports:

- Containers
- Virtual Machines
- Non-container workloads

---

## Real World Example

Production Deployment:

```text
Docker Container
      ↓
Kubernetes Cluster
      ↓
Automatic Scaling
Automatic Recovery
Traffic Management
```

---

# 9.4 Monitoring

## What is Monitoring?

Monitoring is the continuous observation of:

- Applications
- Infrastructure
- Servers
- Networks
- Databases

Monitoring helps companies detect problems early.

---

## Why Monitoring Matters

Without monitoring:

Organizations may not know:

- Server failures
- Memory exhaustion
- API slowdowns
- Application crashes

---

## Common Monitoring Areas

### Infrastructure Monitoring

Tracks:

- CPU usage
- Memory usage
- Disk utilization
- Network traffic

---

### Application Monitoring

Tracks:

- Response time
- Request count
- Error rate
- Throughput

---

### Business Monitoring

Tracks:

- Revenue
- Conversion rates
- User activity

---

## Popular Monitoring Tools

### Grafana

Visualization platform.

Used for:

- Dashboards
- Metrics graphs
- Alert visualization

---

### Prometheus

Metrics collection system.

Collects:

- CPU metrics
- Memory metrics
- Application metrics

---

### Datadog

Enterprise monitoring platform.

Supports:

- Infrastructure monitoring
- Logs
- Metrics
- Tracing

---

## Monitoring Workflow

```text
Application Metrics
        ↓
Prometheus Collection
        ↓
Grafana Dashboards
        ↓
Alerts Generated
```

---

## Real World Example

Production Monitoring:

```text
CPU Usage = 95%
Memory Usage = 90%
API Response Time = 3 seconds
```

Monitoring tools generate alerts for engineers.

---

# 9.5 Security

## What is Deployment Security?

Security ensures applications and infrastructure remain protected against threats, attacks, and unauthorized access.

Modern deployments integrate security throughout the software lifecycle.

---

## Security Best Practices

### Secrets Management

Applications require secrets.

Examples:

- Database passwords
- API keys
- Tokens
- Certificates

Secrets should never be stored in code repositories.

Proper secret storage:

- AWS Secrets Manager
- Vault
- Kubernetes Secrets

---

### IAM Policies

IAM controls permissions.

Defines:

- Who can access resources
- What actions are allowed
- Which resources can be modified

Example:

```text
Developer → Read Access
DevOps Engineer → Deployment Access
Administrator → Full Access
```

---

### Encryption

Protects sensitive data.

Types:

#### Data at Rest

Encrypted storage.

Examples:

- Encrypted database storage
- Encrypted disks

---

#### Data in Transit

Encrypted network communication.

Examples:

- HTTPS
- TLS certificates

---

### Vulnerability Scanning

Security scanning detects software weaknesses.

Scans:

- Container images
- Dependencies
- Operating systems

Popular tools:

- Trivy
- Snyk
- Nessus

---

## Real World Security Flow

```text
Application Code
       ↓
Security Scan
       ↓
Container Scan
       ↓
Deployment Approval
       ↓
Production Release
```

---

# 9.6 Zero-Downtime Deployment

## What is Zero-Downtime Deployment?

Zero-Downtime Deployment allows organizations to release software **without interrupting users**.

The application remains available during deployment.

---

## Why Zero-Downtime Matters

Production downtime may cause:

- Revenue loss
- Customer dissatisfaction
- Business interruption

Modern systems aim for continuous availability.

---

## Common Zero-Downtime Techniques

### Blue-Green Deployment

Two production environments.

```text
Blue → Current Production
Green → New Release
```

Traffic switches after validation.

Advantages:

- Near-zero downtime
- Fast rollback

---

### Rolling Deployment

Servers updated gradually.

Example:

```text
Update 2 servers at a time.
```

Application remains online.

---

### Canary Deployment

Release to small user group first.

Example:

```text
5% Users → New Version
95% Users → Old Version
```

If stable:

```text
100% rollout
```

---

## Modern Deployment Architecture Example

```text
Developer Code Push
        ↓
Git Repository
        ↓
CI/CD Pipeline
        ↓
Docker Build
        ↓
Container Registry
        ↓
Kubernetes Deployment
        ↓
Monitoring + Security Validation
        ↓
Production Release
```

# 10. Conclusion

Deployment is a critical phase in software delivery.

Modern organizations rely on automated, scalable, and reliable deployment systems.

Most used deployment techniques in present companies include:

- Rolling Deployment
- Blue-Green Deployment
- Canary Deployment
- A/B Deployment
- Shadow Deployment

Companies combine these techniques with:

- CI/CD pipelines
- Containers
- Cloud platforms
- Monitoring systems

The goal is simple:

> Deliver software faster, safer, and with minimal downtime.
