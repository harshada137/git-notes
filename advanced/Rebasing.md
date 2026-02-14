# 📂 01 – Rebasing

# 📘 1️⃣ git-rebase-basics.md

## 🔹 What is Git Rebase?

`git rebase` is used to **move or reapply commits from one branch onto another branch**.

It rewrites commit history by placing your changes on top of another base branch.

---

## 🔹 Why Use Rebase?

* To keep a **clean and linear commit history**
* To avoid unnecessary merge commits
* To update a feature branch with latest main branch changes

---

## 🔹 Basic Syntax

```bash
git rebase <branch-name>
```

---

## 🔹 Example Scenario

Assume:

```
main:    A---B---C
feature:      D---E
```

You run:

```bash
git checkout feature
git rebase main
```

After rebase:

```
main:    A---B---C
feature:          D'---E'
```

👉 D and E are replayed on top of C.

---

## 🔹 What Actually Happens?

1. Git temporarily removes your commits
2. Moves branch pointer to latest target branch
3. Reapplies your commits one by one

---

## 🔹 Rebase Current Branch Onto Main

```bash
git checkout feature
git rebase main
```

---

## 🔹 Rebase vs Pull with Rebase

```bash
git pull --rebase
```

Instead of merge commit, it rebases local commits on top of remote.

---

---

# 📘 2️⃣ interactive-rebase.md

## 🔹 What is Interactive Rebase?

Interactive rebase allows you to:

* Edit commits
* Reorder commits
* Squash commits
* Delete commits
* Modify commit messages

---

## 🔹 Command

```bash
git rebase -i HEAD~n
```

Where `n` = number of previous commits to modify.

Example:

```bash
git rebase -i HEAD~3
```

---

## 🔹 Interactive Options

When editor opens:

```
pick   → keep commit
reword → edit commit message
edit   → modify commit
squash → combine with previous commit
fixup  → squash without keeping message
drop   → delete commit
```

---

## 🔹 Example – Squashing

Before:

```
Commit 1: Added login
Commit 2: Fixed typo
Commit 3: Fixed CSS
```

Use interactive rebase and mark commit 2 & 3 as `squash`.

After:

```
Single clean commit: Added login feature
```

---

## 🔹 Use Cases

* Clean messy commits before pushing
* Prepare feature branch for PR
* Rewrite commit history

---

---

# 📘 3️⃣ rebase-vs-merge.md

## 🔹 Git Merge

```bash
git merge feature
```

Creates a merge commit.

History:

```
A---B---C
         \
          D---E
               \
                M (merge commit)
```

---

## 🔹 Git Rebase

```bash
git rebase main
```

History becomes linear:

```
A---B---C---D'---E'
```

---

## 🔹 Key Differences

| Feature                | Merge      | Rebase |
| ---------------------- | ---------- | ------ |
| History                | Non-linear | Linear |
| Merge Commit           | Yes        | No     |
| Safe for shared branch | Yes        | No     |
| Cleaner history        | No         | Yes    |

---

## 🔹 When to Use What?

✅ Use **merge**:

* On shared branches
* On public branches

✅ Use **rebase**:

* On local feature branches
* Before creating pull request

---

---

# 📘 4️⃣ golden-rule-of-rebasing.md

## 🔥 Golden Rule

> ❌ Never rebase a public/shared branch.

---

## 🔹 Why?

Rebase rewrites history.
If others have pulled the branch and you rebase it:

* Commit hashes change
* Causes conflicts
* Creates duplicate commits
* Breaks team workflow

---

## 🔹 Safe Rebase

✔ Rebase only local branches
✔ Rebase before pushing
✔ Avoid rebasing main or shared branch

---

## 🔹 If Already Pushed?

If you rebased and pushed:

```bash
git push --force
```

⚠ Dangerous because it overwrites history.

Better:

```bash
git push --force-with-lease
```

Safer force push.

---

---

# 📘 5️⃣ squashing-commits.md

## 🔹 What is Squashing?

Squashing means combining multiple commits into one.

---

## 🔹 Why Squash?

* Remove unnecessary small commits
* Clean commit history
* Make PR professional

---

## 🔹 How to Squash?

```bash
git rebase -i HEAD~3
```

Change:

```
pick 123 commit1
pick 456 commit2
pick 789 commit3
```

To:

```
pick 123 commit1
squash 456 commit2
squash 789 commit3
```

---

## 🔹 Result

Multiple commits → One meaningful commit

---

## 🔹 Squash During Merge

```bash
git merge --squash feature
```

Creates single commit from feature branch.

---

---

# 📘 6️⃣ rebase-conflicts.md

## 🔹 What is Rebase Conflict?

When Git cannot automatically apply a commit during rebase due to code conflicts.

---

## 🔹 When Does Conflict Occur?

* Same file modified in both branches
* Same lines edited differently

---

## 🔹 Conflict During Rebase Example

```bash
git rebase main
```

Output:

```
CONFLICT (content): Merge conflict in file.txt
```

---

## 🔹 How to Resolve

### Step 1: Open conflicted file

You’ll see:

```
<<<<<<< HEAD
code from main
=======
code from feature
>>>>>>> commit-hash
```

### Step 2: Edit manually and remove markers

### Step 3:

```bash
git add file.txt
git rebase --continue
```

---

## 🔹 Abort Rebase

```bash
git rebase --abort
```

Returns branch to original state.

---

## 🔹 Skip Commit

```bash
git rebase --skip
```

Skips problematic commit.

---

---

# 🧠 Important Interview Points

* Rebase rewrites history
* Merge preserves history
* Interactive rebase is used to clean commits
* Never rebase shared branches
* Use `--force-with-lease` carefully
* Rebase creates new commit hashes

---

# 🔥 Quick Summary

| Topic              | Key Idea                   |
| ------------------ | -------------------------- |
| Rebase Basics      | Move commits to new base   |
| Interactive Rebase | Modify commit history      |
| Rebase vs Merge    | Linear vs merge commit     |
| Golden Rule        | Never rebase public branch |
| Squashing          | Combine commits            |
| Rebase Conflicts   | Manual conflict resolution |


Tell me what you want next 😊

