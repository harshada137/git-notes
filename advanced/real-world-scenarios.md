

# 1️⃣ open-source-contribution

## 🔎 What It Means in GitHub

On GitHub, open-source contribution is done using:

* Forking repositories
* Pull Requests (PRs)
* Code Reviews
* Issues
* Discussions

## ✅ Complete GitHub Workflow

### Step 1: Fork Repository

Click **Fork** button on GitHub.
This creates a copy under your account.

### Step 2: Create New Branch (on GitHub UI or locally)

Contributors never push directly to `main`.

### Step 3: Create Pull Request (PR)

* Compare changes
* Add title & description
* Link related Issue

### Step 4: Code Review

Maintainers:

* Comment on lines
* Request changes
* Approve PR

### Step 5: Merge

Options available:

* Merge commit
* Squash and merge
* Rebase and merge

---

## 🎯 Why Important in Real World

* Safe collaboration
* Structured contribution flow
* Maintainer control over main branch

---

# 2️⃣ team-collaboration

## 🔎 What It Means in GitHub

When multiple developers work on the same repository in GitHub.

## ✅ GitHub Features Used

### 🔹 Branch Protection Rules

* Prevent direct push to main
* Require PR approval
* Require CI checks

### 🔹 Pull Requests for Every Feature

Developers:

* Create feature branch
* Raise PR
* Get review from teammates

### 🔹 Review System

* Approve
* Request changes
* Comment inline

### 🔹 CODEOWNERS File

Automatically assign reviewers.

---

## 🛠 Real Production Practice

* `main` → Production
* `develop` → Integration
* Feature branches → PR → Review → Merge

GitHub ensures:

* No unreviewed code enters production
* Full history of discussions

---

# 3️⃣ hotfix-workflow.md (GitHub)

## 🔎 Scenario

Production bug found.
Immediate fix required.

## ✅ GitHub Hotfix Flow

1. Create hotfix branch from `main`
2. Fix issue
3. Create Pull Request
4. Mark PR as urgent
5. Get fast approval
6. Merge into main
7. Create Release (GitHub Release section)

## 🔹 GitHub Release Feature

After merging:

* Create new release
* Add tag (v1.0.1)
* Add release notes

---

## 🎯 Why GitHub Helps

* PR approval even for hotfix
* Version tagging
* Automated CI/CD triggered on release

---

# 4️⃣ release-management

## 🔎 What It Means

Managing production versions using GitHub features.

## ✅ GitHub Release Tools

### 🔹 Releases Section

Create:

* Version tags
* Release notes
* Attach build artifacts

### 🔹 Tags

Used for:

* Versioning
* Triggering deployments

### 🔹 GitHub Actions

GitHub provides GitHub Actions for:

* CI
* CD
* Automated testing
* Deployment on release

Example:

* Push tag → Trigger deployment workflow

---

## 🔥 Semantic Versioning Example

v2.1.3

* Major
* Minor
* Patch

---

# 5️⃣ monorepo-management

## 🔎 What Is Monorepo in GitHub

Single repository containing multiple projects:

```
/frontend
/backend
/devops
```

## ✅ GitHub Features Used

### 🔹 Folder-based PR Review

Reviewers can comment on specific folders.

### 🔹 Path-Based CI (GitHub Actions)

Trigger workflow only if:

* frontend changes
* backend changes

### 🔹 CODEOWNERS for Different Teams

Example:

* Frontend team reviews frontend folder
* DevOps team reviews infra folder

---

## 🎯 Advantages in GitHub

* Centralized Issues
* Single PR system
* Shared documentation

---

# 6️⃣ migration-strategies

## 🔎 Migration Scenarios in GitHub

### 1️⃣ Move Repo From Another Platform

Example:

* From Bitbucket → GitHub
* From GitLab → GitHub

### 2️⃣ Private to Public Repository

Change visibility.

### 3️⃣ Organization Migration

Move repo to GitHub Organization.

---

## ✅ GitHub Migration Tools

* Import repository feature
* GitHub Enterprise migration tools
* Preserve:

  * Issues
  * PR history
  * Commit history
  * Tags

---

## 🔥 What Needs Reconfiguration

After migration:

* Webhooks
* GitHub Actions
* Branch protection rules
* Secrets
* Environment variables

---

# 💎 Why This Folder Is Important for DevOps

As someone preparing for DevOps:

These scenarios connect directly to:

* CI/CD pipelines
* Production deployments
* Branch protection
* Secure collaboration
* Release automation
* Enterprise repository management

