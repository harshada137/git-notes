## 🔹 What is a Git Submodule?

A **Git submodule** allows you to include another Git repository inside your main repository as a subdirectory.

Instead of copying code manually, you link another repository.

It is commonly used when:

* You depend on an external library.
* You want to share a common project across multiple repos.
* You want to maintain separate version control for a component.

---

## 🔹 How Submodules Work

* The main repository stores:

  * A special file: `.gitmodules`
  * A reference to a **specific commit** of the submodule
* The submodule itself has its own `.git` history.

Important:

> The parent repository does NOT store submodule code history — it only stores a pointer (commit reference).

---

## 🔹 Adding a Submodule

```bash
git submodule add <repo-url> folder-name
```

Example:

```bash
git submodule add https://github.com/user/library.git libs/library
```

This creates:

* `libs/library/`
* `.gitmodules`

Then commit:

```bash
git commit -m "Added submodule"
```

---

## 🔹 Cloning a Repository With Submodules

Normal clone is not enough.

Correct way:

```bash
git clone --recurse-submodules <repo-url>
```

If already cloned:

```bash
git submodule init
git submodule update
```

---

## 🔹 Updating Submodule

To get latest changes from submodule:

```bash
cd submodule-folder
git pull origin main
cd ..
git add submodule-folder
git commit -m "Updated submodule"
```

---

## 🔹 Key Characteristics

✔ Separate repository
✔ Separate commit history
✔ Fixed commit reference
❌ Requires extra commands
❌ Can be confusing for beginners

---

# 2️⃣ working-with-submodules.md

This file explains practical workflows.

---

## 🔹 Everyday Commands

### Check Submodule Status

```bash
git submodule status
```

Shows:

* Current commit
* If modified
* If uninitialized

---

### Update All Submodules

```bash
git submodule update --remote
```

---

### Clone + Initialize in One Step

```bash
git clone --recurse-submodules
```

---

## 🔹 Important Problem

If someone updates the submodule but doesn’t commit the updated pointer in main repo:

Other developers won’t see changes.

Always remember:

```
Update submodule → Commit pointer → Push main repo
```

---

## 🔹 Removing a Submodule

Steps:

```bash
git submodule deinit -f folder
rm -rf .git/modules/folder
git rm -f folder
```

---

## 🔹 Common Issues

| Issue               | Reason                              |
| ------------------- | ----------------------------------- |
| Submodule empty     | Not initialized                     |
| Detached HEAD       | Submodules checkout specific commit |
| Changes not visible | Pointer not committed               |

---

# 3️⃣ git-subtree.md

## 🔹 What is Git Subtree?

Git Subtree is an alternative to submodules.

Instead of linking a repo, it:

* Merges another repository into a subdirectory.
* Keeps its history.
* No extra `.gitmodules` file needed.

It feels like normal Git.

---

## 🔹 Add a Subtree

```bash
git subtree add --prefix=libs/library <repo-url> main --squash
```

Options:

* `--prefix` → folder
* `--squash` → combine commits into one

---

## 🔹 Pull Updates

```bash
git subtree pull --prefix=libs/library <repo-url> main --squash
```

---

## 🔹 Push Back to Original Repo

```bash
git subtree push --prefix=libs/library <repo-url> main
```

---

## 🔹 Characteristics

✔ No separate initialization
✔ Easier for team
✔ Works like normal repo
❌ Repo size increases
❌ History duplication possible

---

# 4️⃣ submodules-vs-subtrees.md

This file compares both approaches.

---

## 🔹 Comparison Table

| Feature                 | Submodule         | Subtree           |
| ----------------------- | ----------------- | ----------------- |
| Separate Repo           | Yes               | No                |
| Commit Pointer          | Yes               | No                |
| Easy for Beginners      | ❌                 | ✔                 |
| Requires Extra Commands | Yes               | No                |
| Repo Size               | Small             | Larger            |
| Best For                | Strict separation | Simple dependency |

---

## 🔹 When to Use Submodule?

* Large shared libraries
* Independent release cycles
* Need strict version control

---

## 🔹 When to Use Subtree?

* Simple dependency
* Small team
* Want easy workflow
* Avoid complexity

---

# 5️⃣ monorepo-strategies.md

This file explains repository organization strategies.

---

## 🔹 What is a Monorepo?

Monorepo = Single repository containing multiple projects.

Example:

```
project/
 ├── frontend/
 ├── backend/
 ├── mobile/
```

Used by large companies.

Examples:

* Google
* Facebook
* Microsoft

---

## 🔹 Monorepo vs Polyrepo

| Monorepo           | Polyrepo           |
| ------------------ | ------------------ |
| One repo           | Multiple repos     |
| Easier refactoring | Clear separation   |
| Single CI/CD       | Separate pipelines |

---

## 🔹 How Submodules/Subtrees Fit

* Submodules → Polyrepo style dependency
* Subtrees → Hybrid approach
* Monorepo → Everything in one repo

---

## 🔹 Strategies

### 1️⃣ Pure Monorepo

All code in one repository.

### 2️⃣ Polyrepo

Each service in separate repository.

### 3️⃣ Hybrid

Main repo + subtree or submodules.

---

# 🎯 Final Understanding

This folder teaches:

* How to manage external repositories
* Different dependency management approaches
* Large-scale repository architecture decisions
* When to choose submodules vs subtrees
* How big companies structure repositories

