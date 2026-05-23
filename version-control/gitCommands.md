# Git Commands

## Introduction

Git commands are used to manage source code, track changes, collaborate with teams, and maintain project history.

This document covers commonly used Git commands in real-world software development.

---

# Git Configuration Commands

## Check Git Version

```bash
git --version
```

Displays installed Git version.

---

## Configure Username

```bash
git config --global user.name "Your Name"
```

---

## Configure Email

```bash
git config --global user.email "your@email.com"
```

---

## View Git Configuration

```bash
git config --list
```

---

# Repository Commands

## Initialize Repository

```bash
git init
```

Creates a new local Git repository.

---

## Clone Repository

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/user/project.git
```

Downloads remote repository to local machine.

---

# File Tracking Commands

## Check Repository Status

```bash
git status
```

Displays:

- modified files
- staged files
- untracked files

---

## Add Single File

```bash
git add file.txt
```

---

## Add All Files

```bash
git add .
```

Adds all changes to staging area.

---

# Commit Commands

## Commit Changes

```bash
git commit -m "commit message"
```

Example:

```bash
git commit -m "Added login functionality"
```

Creates snapshot of changes.

---

## Commit All Tracked Files

```bash
git commit -am "updated code"
```

Shortcut for modified tracked files.

---

# Branch Commands

## View Branches

```bash
git branch
```

---

## Create Branch

```bash
git branch feature-auth
```

---

## Switch Branch

```bash
git checkout feature-auth
```

---

## Create and Switch Branch

```bash
git checkout -b feature-auth
```

---

## Rename Branch

```bash
git branch -m old-name new-name
```

---

## Delete Branch

```bash
git branch -d feature-auth
```

---

# Merge Commands

## Merge Branch

```bash
git merge feature-auth
```

Combines branch changes into current branch.

---

# Remote Repository Commands

## Add Remote Repository

```bash
git remote add origin <repository-url>
```

Example:

```bash
git remote add origin https://github.com/user/project.git
```

---

## View Remote Repositories

```bash
git remote -v
```

---

# Push Commands

## Push Changes

```bash
git push origin main
```

Uploads local commits to remote repository.

---

## Push New Branch

```bash
git push -u origin feature-auth
```

---

## Force Push

```bash
git push --force
```

Dangerous command.

Can overwrite remote history.

Use carefully.

---

# Pull Commands

## Pull Latest Changes

```bash
git pull origin main
```

Downloads and merges latest changes.

---

## Fetch Changes

```bash
git fetch
```

Downloads latest changes without merging.

---

# Log Commands

## View Commit History

```bash
git log
```

---

## One-Line Commit History

```bash
git log --oneline
```

---

## Last 5 Commits

```bash
git log --oneline -5
```

---

# Difference Commands

## View File Changes

```bash
git diff
```

---

## Compare Staged Changes

```bash
git diff --staged
```

---

# Stash Commands

## Save Temporary Changes

```bash
git stash
```

Temporarily stores uncommitted changes.

---

## View Stash List

```bash
git stash list
```

---

## Restore Stash

```bash
git stash apply
```

---

# Reset Commands

## Unstage File

```bash
git reset file.txt
```

---

## Reset Last Commit

```bash
git reset --soft HEAD~1
```

Removes commit but keeps changes.

---

## Hard Reset

```bash
git reset --hard HEAD~1
```

Deletes commit and changes permanently.

Dangerous command.

---

# Restore Commands

## Restore File Changes

```bash
git restore file.txt
```

Discards local modifications.

---

# Tag Commands

## Create Tag

```bash
git tag v1.0
```

---

## Push Tags

```bash
git push origin --tags
```

---

# Rebase Commands

## Rebase Branch

```bash
git rebase main
```

Reapplies commits on top of another branch.

---

# Cherry-Pick Commands

## Copy Specific Commit

```bash
git cherry-pick <commit-id>
```

Applies selected commit to current branch.

---

# Remove Files

## Remove Tracked File

```bash
git rm file.txt
```

---

# Git Ignore

## Create .gitignore

```bash
touch .gitignore
```

Example:

```text
node_modules/
.env
dist/
```

Prevents unnecessary files from being tracked.

---

# Undo Changes

## Undo Last Commit

```bash
git revert HEAD
```

Creates new commit that reverses previous commit.

---

# Useful Real-World Workflow

## Create Feature Branch

```bash
git checkout -b feature-login
```

---

## Add Changes

```bash
git add .
```

---

## Commit Changes

```bash
git commit -m "Added login page"
```

---

## Push Branch

```bash
git push origin feature-login
```

---

## Create Pull Request

Open GitHub and create PR.

---

# Common Git Problems

## Merge Conflict

Occurs when same code section is modified by multiple developers.

---

## Detached HEAD

Occurs when checkout is performed directly on commit.

---

## Accidentally Committed Wrong Files

Use:

```bash
git reset
```

---

# Git Best Practices

## Use Meaningful Commit Messages

Good:

```text
Fixed JWT token validation issue
```

Bad:

```text
fixed bug
```

---

## Use Feature Branches

Avoid working directly on main branch.

---

## Pull Before Push

Always synchronize latest code.

---

## Avoid Force Push on Shared Branches

Can overwrite others' work.

---

## Keep Commits Small

Small commits improve readability and debugging.

---

# Important Git Concepts

| Concept | Description |
|---------|-------------|
| Repository | Project storage |
| Commit | Snapshot of changes |
| Branch | Independent development line |
| Merge | Combine branches |
| Pull Request | Request to merge changes |
| Fork | Copy of repository |
| Clone | Download repository |

---

# Most Frequently Used Commands

```bash
git status
git add .
git commit -m "message"
git pull origin main
git push origin main
git checkout -b branch-name
git log --oneline
```
