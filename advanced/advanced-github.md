# 📂 05 – Advanced GitHub

This section covers advanced features of
👉 GitHub

It includes:

* CI/CD automation
* Hosting
* Project management
* Security
* Package management

Total Topics Covered: **15**

---

# 🚀 1️⃣ GitHub Actions (CI/CD)

Powered by
👉 GitHub Actions

GitHub Actions allows you to automate:

* Build process
* Testing
* Docker image creation
* Deployment to servers/cloud
* CI/CD pipelines

---

## 🔹 Introduction to Actions

GitHub Actions is GitHub’s built-in CI/CD system.

Instead of manually:

* Running tests
* Building applications
* Deploying code

You define automation in a YAML file.

Workflow files are stored inside:

```
.github/workflows/
```

---

## 🔹 Workflows

A workflow is an automated process triggered by events.

Example:

```yaml
name: CI Pipeline

on: push

jobs:
  build:
    runs-on: ubuntu-latest
```

---

## 🔹 Jobs and Steps

### Job

* Runs on a virtual machine (runner)
* Independent execution unit

### Step

Each job contains steps.

```yaml
steps:
  - uses: actions/checkout@v3
  - run: npm install
```

Types:

* `uses:` → reusable action
* `run:` → shell command

---

## 🔹 Triggers and Events

Workflows run based on events:

* push
* pull_request
* workflow_dispatch (manual)
* schedule (cron job)

Example:

```yaml
on:
  schedule:
    - cron: "0 0 * * *"
```

---

## 🔹 Marketplace Actions

Reusable actions available in
👉 GitHub Marketplace

Examples:

* actions/checkout
* setup-node
* docker build actions

---

## 🔹 CI/CD Pipelines

### CI – Continuous Integration

* Code pushed
* Automatically builds
* Runs tests

### CD – Continuous Deployment

* Deploys after successful build
* Can deploy to:

  * AWS
  * Docker Hub
  * Kubernetes
  * VPS

---

# 🌐 2️⃣ GitHub Pages

GitHub Pages allows you to host static websites directly from your repository.

Used for:

* Portfolio websites
* Documentation sites
* Project demos

You can deploy from:

* main branch
* docs folder

---

# 📊 3️⃣ GitHub Projects

Project management tool inside GitHub.

Used for:

* Task tracking
* Kanban boards
* Sprint planning

Helps manage development workflow.

---

# 📖 4️⃣ GitHub Wikis

Documentation feature inside a repository.

Used for:

* Technical documentation
* API documentation
* Internal team docs

---

# 💬 5️⃣ GitHub Discussions

Community discussion feature.

Used for:

* Q&A
* Feature requests
* Idea discussions
* Community support

---

# 🔐 6️⃣ GitHub Security

GitHub provides built-in security tools.

---

## 🔹 Dependabot

Automatically:

* Detects outdated dependencies
* Creates pull requests to update them
* Fixes vulnerable packages

---

## 🔹 Security Advisories

Allows maintainers to:

* Report vulnerabilities privately
* Publish security fixes
* Notify users

---

## 🔹 Code Scanning

Automatically scans code for:

* Security vulnerabilities
* Bugs
* Unsafe patterns

---

## 🔹 Secret Scanning

Detects:

* API keys
* Tokens
* Passwords accidentally committed

Prevents credential leaks.

---

# 📦 7️⃣ GitHub Packages

GitHub’s package hosting service.

Used to:

* Store Docker images
* Store npm packages
* Store Maven/Gradle packages
* Share internal packages securely


