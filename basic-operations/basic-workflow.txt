# Basic Git Workflow - Daily Development Guide

## Introduction

This guide covers the fundamental Git workflow that you'll use daily. Understanding this workflow is essential for effective version control and collaboration.

## The Basic Git Workflow

### Overview
The standard Git workflow follows these stages:

1. **Working Directory** - Where you make changes
2. **Staging Area (Index)** - Where you prepare changes
3. **Repository** - Where changes are permanently stored

```
Working Directory → Staging Area → Repository
    (git add)         (git commit)
```

## Starting Your Work

### Check Repository Status
Always start by checking what's happening:

```bash
# See current state
git status

# Short format
git status -s
```

### Pull Latest Changes
Get updates from remote repository:

```bash
# Pull from current branch
git pull

# Pull with rebase
git pull --rebase

# Fetch first, then merge
git fetch origin
git merge origin/main
```

## Making Changes

### 1. Modify Files
Edit files using your preferred editor or IDE. Git tracks:
- **Modified files** - Existing tracked files that changed
- **New files** - Untracked files you created
- **Deleted files** - Files you removed

### 2. Review Changes
Before staging, review what changed:

```bash
# See all changes
git diff

# See changes in specific file
git diff filename.txt

# See changes with word-level detail
git diff --word-diff
```

## Staging Changes

### Basic Staging
```bash
# Stage single file
git add filename.txt

# Stage multiple files
git add file1.txt file2.txt

# Stage all changes in directory
git add src/

# Stage all changes in repository
git add .
git add -A
```

### Selective Staging
```bash
# Stage only modified and deleted files (not new)
git add -u

# Interactive staging
git add -i

# Patch mode (stage parts of files)
git add -p filename.txt
```

### Review Staged Changes
```bash
# See what's staged
git diff --staged
git diff --cached

# Status with staged/unstaged distinction
git status
```

## Committing Changes

### Basic Commit
```bash
# Commit with inline message
git commit -m "Add user authentication feature"

# Commit with editor for longer message
git commit

# Stage all tracked files and commit
git commit -am "Update documentation"
```

### Good Commit Messages
Follow these conventions:

```bash
# Good format
git commit -m "Fix login bug preventing user access"

# With body
git commit -m "Add password reset feature

- Implement email verification
- Add password strength validation
- Update user settings page"

# Using conventional commits
git commit -m "feat: add user profile page"
git commit -m "fix: resolve memory leak in cache"
git commit -m "docs: update API documentation"
```

### Amending Commits
```bash
# Modify last commit
git commit --amend

# Change last commit message
git commit --amend -m "New message"

# Add forgotten files to last commit
git add forgotten_file.txt
git commit --amend --no-edit
```

## Complete Workflow Example

### Scenario: Adding a New Feature

```bash
# 1. Start with clean state
git status

# 2. Pull latest changes
git pull origin main

# 3. Create feature branch (optional but recommended)
git checkout -b feature/user-profile

# 4. Make changes to files
# ... edit files ...

# 5. Check what changed
git status
git diff

# 6. Stage changes
git add src/profile.js
git add src/styles/profile.css

# 7. Review staged changes
git diff --staged

# 8. Commit with descriptive message
git commit -m "Add user profile page with avatar upload"

# 9. Push to remote
git push origin feature/user-profile
```

## Daily Workflows

### Morning Routine
```bash
# 1. Check current state
git status

# 2. Get latest changes
git pull

# 3. See what others did
git log --since="yesterday" --oneline --all

# 4. Start working
# ... make changes ...
```

### Quick Fix Workflow
```bash
# 1. Check status
git status

# 2. Make fix
# ... edit file ...

# 3. Quick commit
git add -u
git commit -m "fix: resolve navbar alignment issue"

# 4. Push
git push
```

### End of Day Workflow
```bash
# 1. Check what you worked on
git log --since="midnight" --author="$(git config user.name)"

# 2. Commit work in progress if needed
git add .
git commit -m "WIP: user dashboard - needs testing"

# 3. Push to remote
git push

# 4. Check status
git status
```

## Working with Branches

### Create and Switch
```bash
# Create new branch
git branch feature-name

# Switch to branch
git checkout feature-name

# Create and switch (one command)
git checkout -b feature-name

# New syntax (Git 2.23+)
git switch -c feature-name
```

### Branch Workflow
```bash
# 1. Create feature branch
git checkout -b feature/login-page

# 2. Make changes and commit
git add .
git commit -m "Add login form"

# 3. More changes
git add .
git commit -m "Add validation"

# 4. Push branch
git push -u origin feature/login-page

# 5. Switch back to main
git checkout main

# 6. Merge feature
git merge feature/login-page
```

## Handling Mistakes

### Unstaging Files
```bash
# Unstage specific file
git restore --staged filename.txt
# or older syntax
git reset HEAD filename.txt

# Unstage all files
git restore --staged .
git reset HEAD
```

### Discarding Changes
```bash
# Discard changes in specific file
git restore filename.txt
# or older syntax
git checkout -- filename.txt

# Discard all changes
git restore .
git checkout -- .
```

### Undoing Commits
```bash
# Undo last commit, keep changes staged
git reset --soft HEAD~1

# Undo last commit, keep changes unstaged
git reset HEAD~1
git reset --mixed HEAD~1

# Undo last commit, discard changes
git reset --hard HEAD~1
```

## Stashing Work

### Save Work in Progress
```bash
# Stash current changes
git stash

# Stash with message
git stash save "WIP: user authentication"

# Stash including untracked files
git stash -u
```

### Retrieve Stashed Work
```bash
# List stashes
git stash list

# Apply last stash
git stash apply

# Apply and remove from stash list
git stash pop

# Apply specific stash
git stash apply stash@{1}
```

### Stash Workflow
```bash
# 1. Working on feature A
git add .

# 2. Urgent bug fix needed
git stash

# 3. Switch to main branch
git checkout main

# 4. Fix bug
git add .
git commit -m "fix: critical bug"

# 5. Return to feature
git checkout feature-A
git stash pop
```

## Syncing with Remote

### Pushing Changes
```bash
# Push current branch
git push

# Push new branch
git push -u origin branch-name

# Push all branches
git push --all

# Force push (dangerous!)
git push --force
```

### Pulling Changes
```bash
# Pull current branch
git pull

# Pull specific branch
git pull origin main

# Pull without merge commit
git pull --rebase

# Fetch without merging
git fetch origin
```

### Fetch vs Pull
```bash
# Fetch updates from remote
git fetch origin

# See what changed
git log origin/main..main

# Merge updates
git merge origin/main

# This is equivalent to
git pull origin main
```

## Collaboration Workflow

### Fork and Pull Request Workflow
```bash
# 1. Clone repository
git clone https://github.com/user/repo.git

# 2. Create feature branch
git checkout -b feature/new-feature

# 3. Make changes
# ... edit files ...

# 4. Commit changes
git add .
git commit -m "Add new feature"

# 5. Push to your fork
git push origin feature/new-feature

# 6. Create pull request on GitHub/GitLab
```

### Shared Repository Workflow
```bash
# 1. Pull latest
git pull origin main

# 2. Create feature branch
git checkout -b feature/enhancement

# 3. Work and commit
git add .
git commit -m "Add enhancement"

# 4. Keep branch updated
git fetch origin
git rebase origin/main

# 5. Push and create PR
git push origin feature/enhancement
```

## Best Practices

### Commit Frequency
```bash
# Commit logical units of work
git commit -m "Add login validation"
git commit -m "Add password strength meter"
git commit -m "Update login tests"

# Not: "Fixed everything" after 3 days
```

### Commit Message Quality
```bash
# Good messages
"Fix: resolve null pointer in user service"
"Add: user profile editing capability"
"Update: improve error handling in API"

# Bad messages
"fixed stuff"
"changes"
"update"
```

### Regular Syncing
```bash
# Sync frequently
# Beginning of work
git pull

# Every hour or so
git fetch origin

# End of logical work unit
git push
```

## Common Patterns

### Feature Development
```bash
git checkout -b feature/my-feature
# ... work ...
git add .
git commit -m "Add feature"
git push -u origin feature/my-feature
# Create PR
```

### Bug Fix
```bash
git checkout -b fix/bug-description
# ... fix bug ...
git add .
git commit -m "fix: describe bug fix"
git push -u origin fix/bug-description
```

### Experimental Changes
```bash
# Save current work
git stash

# Create experiment branch
git checkout -b experiment

# Try changes
# ... experiment ...

# If good, commit
git add .
git commit -m "Experimental approach works"

# If bad, discard
git checkout main
git branch -D experiment
git stash pop
```

## Troubleshooting

### Merge Conflicts
```bash
# During pull/merge
git pull origin main
# CONFLICT appears

# 1. See conflicted files
git status

# 2. Edit files, resolve conflicts
# Look for <<<<<<, ======, >>>>>>

# 3. Stage resolved files
git add resolved-file.txt

# 4. Complete merge
git commit

# Or abort
git merge --abort
```

### Accidentally Committed to Wrong Branch
```bash
# On wrong-branch with unwanted commit
git log -1
# note the commit hash

# Reset this branch
git reset --hard HEAD~1

# Switch to correct branch
git checkout correct-branch

# Cherry-pick the commit
git cherry-pick <commit-hash>
```

### Lost Work Recovery
```bash
# Find lost commits
git reflog

# Recover commit
git checkout <commit-hash>

# Create branch to save it
git checkout -b recovered-work
```

## Summary Cheatsheet

```bash
# Daily commands
git status              # Check status
git pull               # Get updates
git add .              # Stage changes
git commit -m "msg"    # Commit
git push               # Push to remote

# Branch commands
git branch             # List branches
git checkout -b name   # Create branch
git merge name         # Merge branch

# Undo commands
git restore file       # Discard changes
git restore --staged   # Unstage
git reset HEAD~1       # Undo commit

# Information
git log --oneline      # View history
git diff               # See changes
git diff --staged      # See staged changes
```

