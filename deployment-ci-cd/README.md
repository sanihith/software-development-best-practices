# Deployment and CI/CD

## What is Deployment?

Deployment is the process of releasing software or application changes to an environment where users can access and use it.

Deployment can happen to:

- development environment
- testing environment
- staging environment
- production environment

---

# What is CI/CD?

CI/CD stands for:

- Continuous Integration (CI)
- Continuous Delivery (CD)
- Continuous Deployment (CD)

CI/CD automates software building, testing, and deployment processes.

It improves:

- development speed
- software quality
- release frequency
- reliability

---

# Continuous Integration (CI)

Continuous Integration is the practice of frequently merging code changes into a shared repository.

Each code change automatically triggers:

- build process
- automated testing
- code validation

---

# CI Workflow

```text
Developer Pushes Code
          ↓
Repository Trigger
          ↓
Build Application
          ↓
Run Automated Tests
          ↓
Validate Code
```

---

# Benefits of CI

- early bug detection
- faster feedback
- improved collaboration
- reduced integration problems
- automated testing

---

# Continuous Delivery (CD)

Continuous Delivery ensures code is always ready for deployment.

Deployment to production still requires manual approval.

---

# Continuous Delivery Workflow

```text
Code Commit
    ↓
Build
    ↓
Testing
    ↓
Staging Deployment
    ↓
Manual Approval
    ↓
Production Deployment
```

---

# Benefits of Continuous Delivery

- safer releases
- faster deployment
- reliable deployment process
- lower production risk

---

# Continuous Deployment

Continuous Deployment automatically deploys every successful change directly to production without manual approval.

---

# Continuous Deployment Workflow

```text
Code Commit
    ↓
Build
    ↓
Testing
    ↓
Automatic Production Deployment
```

---

# Difference Between Continuous Delivery and Continuous Deployment

| Continuous Delivery | Continuous Deployment |
|--------------------|----------------------|
| Manual approval required | Fully automated |
| Safer for critical systems | Faster releases |
| Common in enterprises | Common in startups |

---

# CI/CD Pipeline

A CI/CD pipeline is an automated workflow that moves code from development to production.

---

# Typical CI/CD Pipeline Stages

```text
Code
 ↓
Build
 ↓
Test
 ↓
Security Scan
 ↓
Package
 ↓
Deploy
 ↓
Monitor
```

---

# Important CI/CD Components

## Source Control

Stores source code.

Examples:

- GitHub
- GitLab
- Bitbucket

---

## Build Server

Compiles and builds applications.

Examples:

- Jenkins
- GitHub Actions
- GitLab CI

---

## Testing Framework

Runs automated tests.

Examples:

- Jest
- JUnit
- Pytest

---

## Artifact Repository

Stores build artifacts.

Examples:

- Nexus
- Artifactory

---

## Deployment Platform

Hosts applications.

Examples:

- AWS
- Kubernetes
- Docker
- EC2

---

# Types of Deployment

# 1. Recreate Deployment

Old version is completely stopped before new version starts.

---

## Workflow

```text
Stop Old Version
        ↓
Deploy New Version
```

---

## Advantages

- simple
- easy to implement

---

## Disadvantages

- downtime occurs

---

# 2. Rolling Deployment

New version is deployed gradually to servers one by one.

---

## Workflow

```text
Server 1 → Update
Server 2 → Update
Server 3 → Update
```

---

## Advantages

- reduced downtime
- safer deployment

---

## Disadvantages

- deployment takes longer

---

# 3. Blue-Green Deployment

Two identical environments are maintained:

- Blue → current production
- Green → new version

Traffic switches after testing.

---

## Workflow

```text
Users → Blue Environment

Deploy New Version → Green Environment

Switch Traffic → Green
```

---

## Advantages

- near-zero downtime
- quick rollback
- safer releases

---

## Disadvantages

- expensive
- requires duplicate infrastructure

---

# 4. Canary Deployment

New version is released to a small percentage of users first.

---

## Workflow

```text
5% Users → New Version
95% Users → Old Version
```

If stable:

```text
100% Users → New Version
```

---

## Advantages

- low-risk deployment
- real user testing

---

## Disadvantages

- monitoring complexity

---

# 5. Shadow Deployment

New version runs alongside old version but does not serve users directly.

Used for testing production traffic safely.

---

# 6. A/B Testing Deployment

Different users receive different application versions.

Used to test features and user behavior.

---

# Deployment Environments

## Development Environment

Used by developers for coding and testing.

---

## Testing Environment

Used by QA team for validation.

---

## Staging Environment

Production-like environment used before release.

---

## Production Environment

Live environment used by actual users.

---

# Deployment Tools

| Tool | Purpose |
|------|----------|
| Jenkins | CI/CD automation |
| GitHub Actions | GitHub automation |
| GitLab CI/CD | Integrated pipelines |
| ArgoCD | Kubernetes deployment |
| Terraform | Infrastructure automation |
| Ansible | Configuration management |

---

# Popular CI/CD Tools

## Jenkins

Open-source automation server.

---

## GitHub Actions

CI/CD directly integrated with GitHub.

---

## GitLab CI/CD

Built-in GitLab pipeline system.

---

## CircleCI

Cloud-based CI/CD platform.

---

# Containerized Deployment

Applications are packaged inside containers.

Example:

- Docker
- Kubernetes

---

# Cloud Deployment

Applications are deployed to cloud platforms.

Examples:

- AWS EC2
- AWS ECS
- AWS EKS
- Azure
- GCP

---

# Infrastructure as Code (IaC)

Infrastructure is managed using code.

Examples:

- Terraform
- CloudFormation

---

# CI/CD Best Practices

## Automate Testing

Always run automated tests in pipeline.

---

## Keep Pipelines Fast

Slow pipelines reduce productivity.

---

## Use Separate Environments

Development, staging, and production should be isolated.

---

## Monitor Deployments

Track failures and performance issues.

---

## Use Rollback Strategy

Always prepare rollback plan.

---

## Secure Secrets

Never store secrets directly in code.

Use:

- AWS Secrets Manager
- Vault
- Environment Variables

---

# Common CI/CD Problems

## Broken Builds

Occurs when application fails to build.

---

## Failed Deployments

Application deployment fails due to configuration or infrastructure issues.

---

## Environment Drift

Different environments behave differently.

---

## Long Build Times

Reduces developer productivity.

---

# Real-World Example

Developer pushes code:

```text
GitHub
   ↓
GitHub Actions
   ↓
Run Tests
   ↓
Build Docker Image
   ↓
Push to Docker Registry
   ↓
Deploy to Kubernetes
```

---

# Advantages of CI/CD

- faster releases
- reduced manual work
- improved software quality
- automated testing
- faster feedback
- reliable deployments
- reduced production issues

---

# Interview Questions

## What is CI/CD?

CI/CD is an automated process for integrating, testing, and deploying code continuously.

---

## Difference Between CI and CD

| CI | CD |
|----|----|
| Code integration | Deployment automation |
| Build & testing | Delivery & deployment |

---

## What is Blue-Green Deployment?

Blue-Green deployment uses two environments to achieve near-zero downtime deployment.

---

## What is Canary Deployment?

Canary deployment releases new versions gradually to a small set of users before full rollout.

---

# Conclusion

CI/CD is a core modern software engineering practice.

It enables:

- rapid development
- automated deployments
- reliable software delivery
- scalable engineering workflows

Modern DevOps heavily depends on efficient CI/CD pipelines.
