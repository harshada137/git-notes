# 📂 `Troubleshooting`

This folder is dedicated to **real-world Git problems and recovery methods**.

In production (especially in teams using Git + CI/CD), troubleshooting Git issues is VERY important.

Now let’s explain each file:

---

## 📄 `common-errors.md`

This file usually contains:

Typical beginner + intermediate Git errors like:

* `fatal: not a git repository`
* `error: failed to push some refs`
* `merge conflict`
* `detached HEAD`
* `permission denied (publickey)`
* `non-fast-forward updates were rejected`

### 🎯 Purpose:

Quick reference guide for debugging Git errors.

In production:
When CI pipeline fails due to Git issues, these are common causes.

---

## 📄 `merge-conflict-scenarios.md`

This file explains:

* What is a merge conflict?
* When does it happen?
* Example conflict markers:

```bash
<<<<<<< HEAD
Your code
=======
Other branch code
>>>>>>> branch-name
```

### Real-world situations:

* Two developers edited same line
* Feature branch outdated
* Rebase conflict
* Conflict during pull

### 🎯 Production relevance:

If DevOps engineer can’t resolve conflicts → deployment blocked.

---

## 📄 `detached-head-state.md`

This explains the famous:

```bash
You are in 'detached HEAD' state
```

### What is it?

You checked out:

* A commit hash
* A tag
* Or a previous commit

Example:

```bash
git checkout 3f4a9b2
```

Now you're not on a branch.

### Risk:

If you commit here → commits may be lost.

### Recovery:

```bash
git checkout -b new-branch-name
```

### 🎯 Production impact:

Can break CI/CD if build is done from wrong commit reference.

---

## 📄 `authentication-issues.md`

This file handles Git authentication problems.

Common issues:

### 🔹 HTTPS issues:

* Username/password not working
* GitHub password authentication removed

Solution:
Use Personal Access Token (PAT)

### 🔹 SSH issues:

* `Permission denied (publickey)`
* SSH key not added to GitHub
* Wrong SSH config

Fix:

```bash
ssh-keygen
ssh-add
```

### 🎯 Production relevance:

CI/CD pipelines fail if Git repo access fails.

---

## 📄 `push-pull-problems.md`

This handles errors like:

### ❌ Push rejected:

```bash
! [rejected] main -> main (non-fast-forward)
```

Reason:
Your local branch is behind remote.

Fix:

```bash
git pull origin main
```

---

### ❌ Pull error:

```bash
fatal: refusing to merge unrelated histories
```

Fix:

```bash
git pull origin main --allow-unrelated-histories
```

---

### 🎯 Production impact:

If push fails → deployment stops.

---

## 📄 `recovery-techniques.md`

This is VERY IMPORTANT for DevOps engineers 🔥

It explains how to recover from mistakes.

Common recovery commands:

### 🔹 Undo last commit (keep changes):

```bash
git reset --soft HEAD~1
```

### 🔹 Undo last commit (delete changes):

```bash
git reset --hard HEAD~1
```

### 🔹 Recover deleted branch:

```bash
git reflog
git checkout -b branch-name commit-id
```

### 🔹 Recover lost commit:

Using `git reflog`

### 🔹 Stash recovery:

```bash
git stash list
git stash apply
```

