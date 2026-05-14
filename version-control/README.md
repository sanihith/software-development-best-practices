# Version Control

## What is Version Control?

Version control is a system that helps developers track, manage, and organize changes made to source code over time.

It allows teams to:

- collaborate on projects
- track code history
- restore previous versions
- manage multiple features simultaneously
- prevent code conflicts

---

# Why Version Control is Important

Without version control:

- code can be lost
- team collaboration becomes difficult
- tracking changes is hard
- rollback is nearly impossible

With version control:

- every change is recorded
- developers can work independently
- changes can be reviewed safely
- software delivery becomes organized

---

# Types of Version Control Systems

## Local Version Control

Tracks changes on a local machine only.

Example:

- RCS

---

## Centralized Version Control System (CVCS)

Uses a central server.

Examples:

- SVN
- Perforce

### Advantages

- simple workflow
- centralized management

### Disadvantages

- single point of failure
- requires server availability

---

## Distributed Version Control System (DVCS)

Every developer has a complete repository copy.

Examples:

- Git
- Mercurial

### Advantages

- offline work
- faster operations
- better collaboration
- no single point of failure

---

# What is Git?

Git is a distributed version control system used to manage source code efficiently.

Created by:

Linus Torvalds

Git helps developers:

- track changes
- collaborate
- maintain project history
- manage branches
- perform code reviews

---

# Basic Git Workflow

```text
Working Directory
        ↓
Staging Area
        ↓
Local Repository
        ↓
Remote Repository
```

---

# Important Git Terminologies

## Repository

A repository is a storage location containing project files and version history.

### Types

- Local Repository
- Remote Repository

---

## Commit

A commit is a snapshot of changes made to the project.

Example:

```bash
git commit -m "Added login feature"
```

---

## Branch

A branch is an independent line of development.

Used for:

- features
- bug fixes
- experiments

Example:

```bash
git branch feature-auth
```

---

## Merge

Combines changes from one branch into another.

Example:

```bash
git merge feature-auth
```

---

## Clone

Creates a local copy of a remote repository.

Example:

```bash
git clone https://github.com/user/project.git
```

---

## Fork

A fork is a copy of another user's repository into your GitHub account.

Used in open-source contributions.

---

## Pull Request (PR)

A pull request is a request to merge code changes into another branch.

Used for:

- code review
- collaboration
- approval workflows

---

# Common Git Commands

## Initialize Repository

```bash
git init
```

---

## Clone Repository

```bash
git clone <repository-url>
```

---

## Check Status

```bash
git status
```

---

## Add Files

```bash
git add .
```

---

## Commit Changes

```bash
git commit -m "commit message"
```

---

## Push Changes

```bash
git push origin main
```

---

## Pull Latest Changes

```bash
git pull origin main
```

---

## Create Branch

```bash
git checkout -b feature-branch
```

---

## Switch Branch

```bash
git checkout main
```

---

## View Commit History

```bash
git log
```

---

# Branching Strategies

## Main Branch

Contains stable production-ready code.

---

## Development Branch

Contains ongoing development changes.

---

## Feature Branches

Created for individual features.

Example:

```text
feature/login
feature/payment
```

---

# GitHub Workflow

```text
Fork Repository
      ↓
Clone Repository
      ↓
Create Branch
      ↓
Make Changes
      ↓
Commit Changes
      ↓
Push Branch
      ↓
Create Pull Request
      ↓
Code Review
      ↓
Merge
```

---

# Merge Conflicts

A merge conflict occurs when multiple developers modify the same code section.

Git cannot automatically determine which change to keep.

---

# Best Practices

## Write Meaningful Commit Messages

Good:

```text
Added JWT authentication middleware
```

Bad:

```text
fixed stuff
```

---

## Commit Small Changes

Small commits are easier to review and debug.

---

## Pull Before Push

Always update local code before pushing.

```bash
git pull origin main
```

---

## Avoid Direct Commits to Main Branch

Use feature branches.

---

## Review Code Before Merge

Always perform code reviews through pull requests.

---

## Use .gitignore

Prevent unnecessary files from entering repository.

Example:

```text
node_modules/
.env
dist/
```

---

# Common Problems

## Detached HEAD

Occurs when checking out a commit directly instead of a branch.

---

## Merge Conflict

Occurs when Git cannot automatically merge changes.

---

## Accidental Force Push

Can overwrite repository history.

Use carefully:

```bash
git push --force
```

---

# Real-World Example

Suppose three developers work on:

- authentication
- payments
- notifications

Each developer creates separate branches:

```text
feature/auth
feature/payment
feature/notifications
```

After testing and review, changes are merged into main branch.

This prevents conflicts and improves collaboration.

---

# Advantages of Version Control

- better collaboration
- safer development
- rollback capability
- history tracking
- parallel development
- easier debugging
- release management

---

# Popular Platforms

- GitHub
- GitLab
- Bitbucket

---

# Interview Questions

## What is Version Control?

Version control is a system that tracks changes to files and helps teams collaborate safely.

---

## Difference Between Git and GitHub

| Git | GitHub |
|-----|--------|
| Version control tool | Hosting platform |
| Local operations | Cloud platform |
| Tracks changes | Stores repositories |

---

## What is a Pull Request?

A pull request is a request to merge code changes after review.

---

# Conclusion

Version control is one of the most important practices in software engineering.

It enables:

- collaboration
- code safety
- team productivity
- scalable development workflows

Git is the industry-standard version control system used in modern software development.