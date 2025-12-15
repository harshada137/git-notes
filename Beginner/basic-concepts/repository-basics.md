# Repository Basics

A **Git repository** is the foundation of version control in Git. It is the place where Git stores all information about a project, including its history, configuration, and tracked files.

---

## What is a Repository?

A repository (often called a *repo*) is a directory that Git uses to track changes. It consists of:

* Project files (source code, scripts, documentation, assets)
* A hidden `.git` directory that contains all Git metadata

The `.git` directory stores:

* Commit history
* Branch and tag information
* Configuration settings
* Staging area data

If the `.git` directory is removed, the project is no longer a Git repository.

---

## Types of Git Repositories

### Local Repository

* Exists on a developer’s local system
* Used for writing and testing code
* Created using `git init` or `git clone`

### Remote Repository

* Hosted on servers like GitHub, GitLab, or Bitbucket
* Used for collaboration and backup
* Accessed through the internet or internal networks

---

## Creating a Repository

### Initialize a New Repository

```bash
git init
```

This command:

* Creates a `.git` directory
* Starts tracking the project

### Clone an Existing Repository

```bash
git clone <repository-url>
```

This command:

* Copies the entire project
* Includes full commit history

---

## Repository Structure

* `.git/` → Git internal data (hidden)
* Project files → Actual working files

Git operations depend entirely on the `.git` folder.

---

## Why Repository Basics Are Important

* Enables version control
* Maintains full project history
* Supports collaboration
* Allows rollback and recovery
* Forms the base for branching and merging

---

## Summary

* A repository is the core of Git
* `.git` directory controls versioning
* Repositories can be local or remote
* All Git workflows depend on repositories
