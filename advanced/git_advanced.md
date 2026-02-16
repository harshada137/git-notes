# 1️⃣ `git-cherry-pick.md`

## 🔹 What is Cherry Pick?

`git cherry-pick` allows you to **apply a specific commit from one branch to another branch**.

Instead of merging the entire branch, you copy only the required commit.

---

## 🔹 Syntax

```bash
git cherry-pick <commit-hash>
```

---

## 🔹 Example

```bash
git checkout main
git cherry-pick a1b2c3d
```

This copies commit `a1b2c3d` into `main`.

---

## 🔹 When to Use?

* A bug fix done in `dev` needs to go to `main`
* You don’t want to merge the full branch
* Hotfixes in production

---

## ⚠️ Important

* It creates a **new commit** (not the same hash).
* Conflicts may occur → resolve manually.

---

# 2️⃣ `git-stash.md`

## 🔹 What is Git Stash?

`git stash` temporarily saves your uncommitted changes and cleans your working directory.

Useful when you need to switch branches quickly.

---

## 🔹 Basic Commands

```bash
git stash
git stash list
git stash apply
git stash pop
git stash drop
```

---

## 🔹 Example Workflow

```bash
git stash
git checkout main
git pull
git checkout feature
git stash pop
```

---

## 🔹 When to Use?

* Switching branches without committing
* Pulling latest changes safely
* Temporary work pause

---

# 3️⃣ `git-tag.md`

## 🔹 What is Git Tag?

Tags are used to mark specific points in history (usually releases).

Example:

* v1.0
* v2.0
* production-release

---

## 🔹 Create Tag

```bash
git tag v1.0
```

Push tag:

```bash
git push origin v1.0
```

Push all tags:

```bash
git push --tags
```

---

## 🔹 Why Tags Matter in DevOps?

* CI/CD triggers
* Versioning
* Release management

---

# 4️⃣ `annotated-vs-lightweight-tags.md`

## 🔹 Lightweight Tag

Just a pointer to a commit.

```bash
git tag v1.0
```

* No metadata
* Simple reference

---

## 🔹 Annotated Tag

Stores extra information:

* Tagger name
* Date
* Message
* Can be signed

```bash
git tag -a v1.0 -m "Release version 1.0"
```

---

## 🔹 Difference Table

| Feature                 | Lightweight | Annotated |
| ----------------------- | ----------- | --------- |
| Metadata                | ❌ No        | ✅ Yes     |
| Message                 | ❌ No        | ✅ Yes     |
| Recommended for release | ❌           | ✅         |

👉 **Use annotated tags for production releases.**

---

# 5️⃣ `git-blame.md`

## 🔹 What is Git Blame?

`git blame` shows **who modified each line of a file and when**.

---

## 🔹 Syntax

```bash
git blame filename
```

---

## 🔹 Output Example

```
a1b2c3d (Harshada 2025-02-10) const app = express();
```

Shows:

* Commit hash
* Author
* Date
* Line content

---

## 🔹 When to Use?

* Debugging
* Finding who introduced a bug
* Understanding code history

⚠️ Not for blaming people 😄 — only for tracking changes.

---

# 6️⃣ `git-bisect.md`

## 🔹 What is Git Bisect?

`git bisect` helps find the commit that introduced a bug using **binary search**.

---

## 🔹 Why It’s Powerful?

If you have:
1000 commits

Instead of checking all 1000 manually,
Git checks only ~10 steps (log₂ 1000 ≈ 10).

---

## 🔹 How It Works

```bash
git bisect start
git bisect bad
git bisect good <good-commit>
```

Git will checkout commits one by one.

You test and tell Git:

```bash
git bisect good
```

or

```bash
git bisect bad
```

After several steps → Git identifies the faulty commit.

End process:

```bash
git bisect reset
```

---

# 🔥 Real DevOps Usage

| Command     | Real Use Case           |
| ----------- | ----------------------- |
| cherry-pick | Hotfix to production    |
| stash       | Temporary work saving   |
| tag         | CI/CD release trigger   |
| blame       | Code debugging          |
| bisect      | Finding breaking commit |

---

# 🎯 Summary

These advanced operations help you:

* Work smarter in multi-branch projects
* Handle production fixes
* Track code history
* Manage releases
* Debug efficiently


