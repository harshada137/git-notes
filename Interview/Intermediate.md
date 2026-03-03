
### 1️⃣ What is the difference between `git merge` and `git rebase`?

**git merge** combines two branches and creates a new merge commit. It preserves the complete branch history.

**git rebase** moves or reapplies commits from one branch onto another. It rewrites commit history to create a linear structure.

* Merge → Safe for shared branches
* Rebase → Clean history for feature branches
* Rebase should not be used on already shared branches

---

### 2️⃣ What is a Pull Request in GitHub?

A **Pull Request (PR)** is a feature in GitHub that allows developers to propose changes before merging into a branch.

It enables:

* Code review
* Discussion
* CI/CD checks
* Approval workflows

PRs are essential in team collaboration and production workflows.

---

### 3️⃣ What are Branch Protection Rules?

Branch Protection Rules in GitHub prevent direct modifications to important branches like `main`.

They can enforce:

* Mandatory pull requests
* Required code reviews
* Required CI checks
* Restrict force pushes

This ensures production stability.

---

### 4️⃣ What is the difference between Fork and Clone?

**Fork** creates a copy of a repository under your GitHub account.
**Clone** downloads a repository to your local machine.

Fork is mainly used for open-source contributions.
Clone is used for local development.

---

### 5️⃣ What is Squash and Merge?

Squash and Merge combines all commits from a Pull Request into a single commit before merging.

Benefits:

* Clean commit history
* Avoids unnecessary commit clutter
* Easier rollback

Commonly used in feature-based workflows.

---

### 6️⃣ What is Git Reflog?

`git reflog` records all changes to the HEAD pointer.

It helps to:

* Recover deleted commits
* Restore accidentally reset branches
* Undo hard resets

It is extremely useful in recovery situations.

---

### 7️⃣ What is a Detached HEAD state?

Detached HEAD occurs when you checkout a specific commit instead of a branch.

In this state:

* You are not on any branch
* New commits are not attached to a branch unless you create one

It is mostly used for testing older commits.

---

### 8️⃣ What is the difference between git reset and git revert?

**git reset**

* Rewrites commit history
* Removes commits
* Dangerous in shared branches

**git revert**

* Creates a new commit that undoes changes
* Preserves history
* Safe for shared branches

For production branches, revert is preferred.

---

### 9️⃣ What is Semantic Versioning?

Semantic Versioning follows this format:

```
MAJOR.MINOR.PATCH
```

Example:

```
v2.1.4
```

* Major → Breaking changes
* Minor → New features
* Patch → Bug fixes

Used during releases in GitHub.

---

### 🔟 What is GitHub Actions?

GitHub Actions is the built-in CI/CD automation tool in GitHub.

It allows:

* Automated testing
* Build pipelines
* Docker image creation
* Deployment workflows

Workflows are triggered by:

* Push
* Pull Request
* Tag creation

---

### 1️⃣1️⃣ What is Git LFS?

Git Large File Storage (LFS) is used to manage large files like:

* Videos
* Binaries
* ML models

Instead of storing large files in repository history, Git LFS stores references and keeps the repository lightweight.

---

### 1️⃣2️⃣ What is the purpose of Tags in Git?

Tags mark specific points in history, usually for releases.

Types:

* Lightweight tag
* Annotated tag (includes metadata like author, date, message)

Tags are commonly used for production versioning.

---

### 1️⃣3️⃣ What is CODEOWNERS in GitHub?

CODEOWNERS is a file in GitHub that automatically assigns reviewers to Pull Requests based on file paths.

It ensures:

* Mandatory expert review
* Controlled ownership
* Faster approval process

Used in enterprise repositories.

---

### 1️⃣4️⃣ What is a Rebase Workflow in Teams?

In a rebase workflow:

* Developers rebase their feature branch onto updated `main`
* This avoids unnecessary merge commits
* Keeps history linear

It is preferred in teams that want a clean commit graph.

---

### 1️⃣5️⃣ Explain a Production-Ready GitHub Workflow.

A typical production workflow includes:

* Feature branch creation
* Pull Request submission
* Code review and approval
* CI/CD checks via GitHub Actions
* Merge into protected main branch
* Tag creation for release
* Deployment triggered automatically

This ensures:

* Code quality
* Stability
* Traceability
* Automation

