
# 1️⃣ What is the difference between `git merge` and `git rebase`?

### ✅ Answer:

* **Merge** creates a new merge commit and preserves branch history.
* **Rebase** rewrites history by placing your changes on top of another branch.

✔ Use **merge** for shared branches.
✔ Use **rebase** for cleaner history before merging feature branches.

In GitHub, both appear differently in Pull Requests.

---

# 2️⃣ What is a Pull Request in GitHub?

### ✅ Answer:

A Pull Request (PR) is a GitHub feature that:

* Proposes changes
* Enables code review
* Triggers CI checks
* Allows discussion before merging

It ensures controlled collaboration before merging into `main`.

---

# 3️⃣ What are Branch Protection Rules in GitHub?

### ✅ Answer:

Branch protection prevents:

* Direct pushes to `main`
* Merging without approval
* Merging without passing CI

Used in production to maintain code stability.

---

# 4️⃣ What is the difference between Fork and Clone?

### ✅ Answer:

* **Fork** → Creates a copy of a repository under your GitHub account.
* **Clone** → Downloads repository to your local system.

Fork is used in open-source contribution workflows.

---

# 5️⃣ What are Git Hooks?

### ✅ Answer:

Git Hooks are scripts that run automatically before or after events like:

* commit
* push
* merge

Example:

* `pre-commit` → Run linting
* `pre-push` → Run tests

In GitHub, CI tools replace local hooks for team-wide enforcement.

---

# 6️⃣ How do you resolve merge conflicts?

### ✅ Answer:

1. Identify conflicting files.
2. Manually fix conflict markers.
3. Stage resolved files.
4. Complete merge.

On GitHub, conflicts can also be resolved directly in the PR UI.

---

# 7️⃣ What is Squash and Merge in GitHub?

### ✅ Answer:

Squash combines all commits from a PR into a single commit before merging.

Benefits:

* Clean commit history
* Avoids unnecessary multiple commits

Commonly used in feature branches.

---

# 8️⃣ What is Git Reflog?

### ✅ Answer:

`git reflog` tracks all movements of HEAD.

Used to:

* Recover deleted commits
* Restore accidentally reset branches

Very useful in production recovery scenarios.

---

# 9️⃣ What is Semantic Versioning?

### ✅ Answer:

Format:

```
MAJOR.MINOR.PATCH
```

Example:

```
v2.3.1
```

* Major → Breaking change
* Minor → New feature
* Patch → Bug fix

Used during GitHub Releases.

---

# 🔟 What is GitHub Actions?

### ✅ Answer:

GitHub Actions is CI/CD automation inside GitHub.

It:

* Runs tests on PR
* Builds Docker images
* Deploys to cloud
* Automates workflows

Triggered by:

* Push
* Pull request
* Tag creation

---

# 1️⃣1️⃣ What is a Detached HEAD state?

### ✅ Answer:

Detached HEAD occurs when:

* You checkout a specific commit instead of a branch.

Changes made here are not attached to any branch unless you create one.

---

# 1️⃣2️⃣ How do you revert a pushed commit?

### ✅ Answer:

Use:

```
git revert <commit-id>
```

It creates a new commit that undoes changes.

Safer than:

```
git reset --hard
```

For shared branches, always use **revert**, not reset.

---

# 1️⃣3️⃣ What is the difference between `git reset` and `git revert`?

### ✅ Answer:

| git reset                  | git revert            |
| -------------------------- | --------------------- |
| Rewrites history           | Preserves history     |
| Dangerous in shared branch | Safe in shared branch |
| Removes commits            | Adds new undo commit  |

---

# 1️⃣4️⃣ What is Git LFS?

### ✅ Answer:

Git Large File Storage is used to manage:

* Large binaries
* Media files
* ML models

Instead of storing large files in repo history, it stores references.

Supported in GitHub repositories.

---

# 1️⃣5️⃣ Explain a Production-Ready Git Workflow.

### ✅ Answer:

Typical GitHub Production Flow:

1. Feature branch created
2. PR raised
3. Code review required
4. CI checks must pass
5. Merge into develop
6. Release branch created
7. Tag version
8. Deploy via CI/CD
9. Hotfix branch if needed

Branch protection + CI + PR approvals ensure stability.

---
