# 📂 04 - Undoing Changes in Git

Undoing changes in Git can happen at **3 levels**:

1. **Working Directory** (before staging)
2. **Staging Area (Index)**
3. **Committed History**

Understanding the difference is very important.

---

# 📄 1️⃣ git-checkout-files.md

## 🔹 What is `git checkout` (for files)?

Before Git 2.23, `git checkout` was used to:

* Switch branches
* Restore files

Now it's mostly replaced by `git restore` (for files) and `git switch` (for branches).

---

## 🔹 Undo Changes in Working Directory

### 👉 Discard changes in a file (not staged)

```bash
git checkout -- filename
```

### Example:

```bash
git checkout -- app.py
```

🔹 What happens?

* Replaces `app.py` with last committed version
* Local changes are permanently deleted

⚠️ Warning: Cannot recover unless committed before.

---

## 🔹 Restore file from specific commit

```bash
git checkout <commit-id> -- filename
```

Example:

```bash
git checkout 34f5a2c -- app.py
```

This restores the file from that commit into working directory.

---

## 🔹 Why discouraged now?

Because `git checkout` does too many things.
Git introduced:

* `git restore`
* `git switch`

---

# 📄 2️⃣ git-reset.md

## 🔹 What is `git reset`?

Used to:

* Unstage files
* Move HEAD pointer
* Delete commits (locally)

⚠️ Dangerous command if misused.

---

## 🔹 Three Types of Reset

### 1️⃣ Soft Reset

```bash
git reset --soft HEAD~1
```

✔ Removes last commit
✔ Keeps changes staged
✔ Keeps working directory intact

👉 Only moves HEAD pointer

---

### 2️⃣ Mixed Reset (Default)

```bash
git reset HEAD~1
```

or

```bash
git reset --mixed HEAD~1
```

✔ Removes last commit
✔ Unstages changes
✔ Keeps working directory

👉 Most commonly used

---

### 3️⃣ Hard Reset (Dangerous)

```bash
git reset --hard HEAD~1
```

✔ Deletes commit
✔ Deletes staged changes
✔ Deletes working directory changes

🚨 Everything gone permanently (unless in reflog)

---

## 🔹 Reset Specific File (Unstage)

```bash
git reset filename
```

Removes file from staging area.

---

## 🔹 When to Use Reset?

* Local commit mistake
* Rewriting local history
* Cleaning staging area

❌ Avoid on shared/public branches

---

# 📄 3️⃣ git-revert.md

## 🔹 What is `git revert`?

Creates a **new commit** that reverses previous commit changes.

✔ Safe
✔ Used for public/shared branches
✔ Does NOT delete history

---

## 🔹 Revert Last Commit

```bash
git revert HEAD
```

Git opens editor → Add commit message → Save.

---

## 🔹 Revert Specific Commit

```bash
git revert <commit-id>
```

---

## 🔹 What Happens Internally?

If commit added:

```python
print("Hello")
```

Revert creates new commit removing it.

History stays intact:

```
A → B → C → D
          ↓ revert
A → B → C → D → E
```

E undoes D.

---

## 🔹 When to Use Revert?

* On production branch
* On shared GitHub branch
* When you don't want to rewrite history

---

# 📄 4️⃣ git-restore.md

Introduced in Git 2.23.

Used only for restoring files.

---

## 🔹 Restore Working Directory Changes

```bash
git restore filename
```

Same as:

```bash
git checkout -- filename
```

---

## 🔹 Unstage a File

```bash
git restore --staged filename
```

Equivalent to:

```bash
git reset filename
```

---

## 🔹 Restore from Specific Commit

```bash
git restore --source=<commit-id> filename
```

Example:

```bash
git restore --source=34f5a2c app.py
```

---

## 🔹 Why Git Introduced Restore?

To separate:

* File restoration
* Branch switching

Cleaner and safer design.

---

# 📄 5️⃣ reset-vs-revert.md

This is VERY IMPORTANT 🔥

| Feature               | git reset  | git revert  |
| --------------------- | ---------- | ----------- |
| Deletes commit?       | Yes        | No          |
| Creates new commit?   | No         | Yes         |
| Safe for shared repo? | ❌ No       | ✅ Yes       |
| Rewrites history?     | Yes        | No          |
| Used for              | Local undo | Public undo |

---

## 🔹 Example Scenario

### 🔸 You pushed wrong commit to GitHub

❌ Don't use:

```bash
git reset --hard
git push --force
```

Because it rewrites history.

✔ Instead use:

```bash
git revert <commit-id>
git push
```

---

## 🔹 Golden Rule

* Private branch → `reset`
* Shared branch → `revert`

---

# 📄 6️⃣ amending-commits.md

## 🔹 What is Amend?

Modify last commit.

---

## 🔹 Change Last Commit Message

```bash
git commit --amend
```

Opens editor → Change message → Save.

---

## 🔹 Add Forgotten File to Last Commit

```bash
git add forgotten-file.py
git commit --amend
```

This updates previous commit.

---

## 🔹 Important Note

Amend rewrites history.

❌ Do NOT amend after pushing (unless force push)

---

## 🔹 When to Use?

* Typo in commit message
* Forgot to add a file
* Small correction in last commit

---

# 🧠 Visual Understanding of Undo Levels

```
Working Directory → Staging Area → Repository
```

| Level           | Undo Command         |
| --------------- | -------------------- |
| Working         | git restore          |
| Staging         | git restore --staged |
| Commit (local)  | git reset            |
| Commit (public) | git revert           |

---

# 🚀 Interview-Level Questions

1. Difference between reset and revert?
2. What happens internally in git revert?
3. Explain soft, mixed, hard reset.
4. How to undo pushed commit safely?
5. What is HEAD~1?
6. What is reflog?

---

# 🔥 Advanced Tip: Recover Lost Commits

If you used hard reset accidentally:

```bash
git reflog
```

Find commit id → restore:

```bash
git reset --hard <commit-id>
```

---

# ✅ Final Summary

| Situation                  | Command                   |
| -------------------------- | ------------------------- |
| Discard file changes       | git restore file          |
| Unstage file               | git restore --staged file |
| Delete last commit (local) | git reset                 |
| Undo pushed commit         | git revert                |
| Fix last commit            | git commit --amend        |


