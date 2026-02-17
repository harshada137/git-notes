# 🔹 1️⃣ git-objects.md

### 📌 Core Idea

Everything in Git is stored as an **object**.

Git is a **content-addressable filesystem**.

Each object:

* Is identified by a SHA-1 hash
* Stored inside `.git/objects/`
* Immutable (never changes)

Example:

```bash
echo "hello" | git hash-object --stdin
```

Git stores the content using its hash:

```
.git/objects/ab/cdef12345...
```

---

### 🎯 Types of Git Objects

There are **4 types**:

1. Blob
2. Tree
3. Commit
4. Tag

Git stores EVERYTHING using these.

---

# 🔹 2️⃣ blobs-trees-commits.md

Let’s break them down.

---

## 📄 Blob (Binary Large Object)

* Stores file content
* Does NOT store filename
* Does NOT store directory structure

Example:
If you create:

```python
print("Hello")
```

Git stores:

* The content as a **blob**
* Hashed version of that content

---

## 🌳 Tree

* Represents a directory
* Stores:

  * Filenames
  * Blob references
  * Subdirectories (other trees)

Think of tree as a **folder snapshot**.

---

## 📌 Commit

* Points to a tree
* Contains:

  * Author
  * Commit message
  * Timestamp
  * Parent commit

Commit = snapshot of your project at that time.

---

### 🧠 Relationship

```
Commit → Tree → Blob
```

So when you commit:
Git stores:

* File content (blob)
* Folder structure (tree)
* Snapshot pointer (commit)

---

# 🔹 3️⃣ references.md

References are pointers to commits.

Instead of remembering:

```
a93jd8293jd82jd82j...
```

Git uses:

```
main
develop
feature/login
```

These are stored inside:

```
.git/refs/
```

Types:

* Branch references
* Tag references
* Remote references

---

# 🔹 4️⃣ head-and-branches.md

## 📌 What is HEAD?

`HEAD` is a pointer to the current branch.

File:

```
.git/HEAD
```

It usually contains:

```
ref: refs/heads/main
```

Meaning:
HEAD → main → commit

---

## 🔄 Detached HEAD

If you checkout a specific commit:

```bash
git checkout <commit-hash>
```

Now HEAD points directly to commit.

This is called:
**Detached HEAD state**

---

## 🧠 How Branches Work

A branch is just:

> A movable pointer to a commit.

When you commit:

* Branch pointer moves forward.

Example:

```
A → B → C
         ↑
        main
```

---

# 🔹 5️⃣ git-directory-structure.md

Inside `.git/` folder:

```
.git/
│── HEAD
│── config
│── description
│── hooks/
│── info/
│── objects/
│── refs/
│── logs/
```

---

## 📂 Important Folders

### objects/

Stores:

* Blobs
* Trees
* Commits

### refs/

Stores:

* Branch pointers
* Tags

### config

Repository configuration

### hooks/

Client-side Git scripts (like pre-commit hook)

---

# 🔹 6️⃣ packfiles.md

When repository grows large:
Storing each object separately becomes inefficient.

Git compresses objects into:

```
.git/objects/pack/
```

These are:

* `.pack` files (compressed objects)
* `.idx` files (index files)

---

## 📌 Why Packfiles?

* Save disk space
* Improve performance
* Used when pushing/pulling

Run:

```bash
git gc
```

Git automatically packs objects.

---

# 🔹 7️⃣ garbage-collection.md

Git doesn’t immediately delete unused objects.

It marks them as unreachable.

Later, during:

```bash
git gc
```

Git:

* Cleans unreachable objects
* Compresses objects
* Optimizes repository

---

## 🧠 Example

If you:

```bash
git commit
git reset --hard HEAD~1
```

That commit still exists in:

* reflog
* objects

Until garbage collection runs.

---

# 🔥 Big Picture

Git is not just version control.
It is:

> A content-addressable database + filesystem + pointer system

Everything is:

* Immutable
* Hash-based
* Snapshot-based (not diff-based)
