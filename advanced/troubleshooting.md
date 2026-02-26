# 📘 Git Troubleshooting Guide (Complete)

# 1️⃣ Common Git Errors

## ❌ Error: `fatal: not a git repository`

**Cause:** You are not inside a Git repository.

**Fix:**

```bash
git init
```

or move into the correct project directory.

---

## ❌ Error: `failed to push some refs`

**Cause:** Remote branch has new commits you don’t have locally.

**Fix:**

```bash
git pull origin main
git push origin main
```

---

## ❌ Error: `permission denied (publickey)`

**Cause:** SSH key not configured.

**Fix:**

```bash
ssh-keygen
ssh-add ~/.ssh/id_rsa
```

Add the public key to GitHub/GitLab.

---

## ❌ Error: `non-fast-forward updates were rejected`

**Cause:** Local branch is behind remote.

**Fix:**

```bash
git pull origin main
```

---

# 2️⃣ Merge Conflict Scenarios

## 🔹 What is a Merge Conflict?

Occurs when:

* Two developers edit the same line
* Branch is outdated
* Rebase conflict occurs

---

## 🔹 Conflict Markers Example

```bash
<<<<<<< HEAD
Your code
=======
Other branch code
>>>>>>> branch-name
```

---

## 🔹 How to Resolve

1. Open conflicted file
2. Remove conflict markers
3. Choose correct code
4. Add & commit

```bash
git add .
git commit
```

---

# 3️⃣ Detached HEAD State

## 🔹 What is Detached HEAD?

Occurs when you checkout:

* Commit hash
* Tag
* Old commit

Example:

```bash
git checkout 3f4a9b2
```

Now you are not on a branch.

---

## 🔹 Why It’s Risky?

Commits made here may be lost.

---

## 🔹 Fix

Create a branch:

```bash
git checkout -b new-branch-name
```

---

# 4️⃣ Authentication Issues

## 🔹 HTTPS Authentication Problem

GitHub removed password authentication.

Use Personal Access Token (PAT).

When prompted for password → enter token.

---

## 🔹 SSH Authentication Issue

Error:

```bash
Permission denied (publickey)
```

### Fix:

Generate SSH key:

```bash
ssh-keygen
```

Add SSH key:

```bash
ssh-add ~/.ssh/id_rsa
```

Copy public key:

```bash
cat ~/.ssh/id_rsa.pub
```

Add it to GitHub → Settings → SSH Keys.

---

# 5️⃣ Push & Pull Problems

---

## ❌ Push Rejected

```bash
! [rejected] main -> main (non-fast-forward)
```

### Fix:

```bash
git pull origin main
git push origin main
```

---

## ❌ Refusing to Merge Unrelated Histories

```bash
fatal: refusing to merge unrelated histories
```

### Fix:

```bash
git pull origin main --allow-unrelated-histories
```

---

## ❌ Cannot Pull Because of Local Changes

Fix:

```bash
git stash
git pull
git stash apply
```

---

# 6️⃣ Recovery Techniques (Very Important)

---

## 🔹 Undo Last Commit (Keep Changes)

```bash
git reset --soft HEAD~1
```

---

## 🔹 Undo Last Commit (Delete Changes)

```bash
git reset --hard HEAD~1
```

---

## 🔹 Recover Deleted Branch

```bash
git reflog
git checkout -b branch-name commit-id
```

---

## 🔹 Recover Lost Commit

```bash
git reflog
```

Find commit hash and restore:

```bash
git checkout commit-id
```

---

## 🔹 Stash Recovery

See stash list:

```bash
git stash list
```

Apply stash:

```bash
git stash apply
```

Delete stash:

```bash
git stash drop
```

---

# 🎯 Most Important Commands for DevOps

| Situation                                 | Command      |
| ----------------------------------------- | ------------ |
| Check history                             | `git log`    |
| Check current branch                      | `git branch` |
| See commit history including deleted refs | `git reflog` |
| Undo commit                               | `git reset`  |
| Safely undo commit (public branch)        | `git revert` |
| Temporarily save changes                  | `git stash`  |

