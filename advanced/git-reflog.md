## 📌 What is Git Reflog?

`git reflog` (Reference Log) records **all movements of HEAD** in your local repository.

Even if you:

* Delete a branch
* Reset hard
* Rebase
* Amend commits

👉 Git still keeps track internally using **reflog**.

---

## 🔎 Why is it Important?

Because it helps you:

* Recover lost commits
* Undo accidental `reset --hard`
* Restore deleted branches

---

## 📌 Command

```bash
git reflog
```

Example output:

```
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
d4e5f6g HEAD@{1}: commit: Added login feature
```

---

## 📌 Recover from Reset

If you accidentally did:

```bash
git reset --hard HEAD~1
```

Recover using:

```bash
git reflog
git reset --hard HEAD@{1}
```

---

## 🧠 Important Notes

* Reflog is **local only**
* Stored in `.git/logs/`
* Entries expire (default 90 days)

---

# 🔹 2. recovering-lost-commits.md

Lost commits happen due to:

* `git reset --hard`
* `git rebase`
* Deleted branch
* Force push

---

## 📌 Methods to Recover

### 1️⃣ Using Reflog

```bash
git reflog
git checkout <commit-id>
```

---

### 2️⃣ Using fsck (deep recovery)

```bash
git fsck --lost-found
```

Shows dangling commits.

---

### 3️⃣ Recover Deleted Branch

```bash
git reflog
git checkout -b recovered-branch <commit-id>
```

---

## ⚠️ Important

If garbage collection runs and commit is unreachable for long, it may be permanently deleted.

---

# 🔹 3. git-filter-branch.md

## 📌 What is git filter-branch?

Used to **rewrite entire Git history**.

Examples:

* Remove sensitive file
* Change author email
* Remove large files
* Modify commit messages

---

## Example: Change Email in Entire History

```bash
git filter-branch --env-filter '
if [ "$GIT_AUTHOR_EMAIL" = "old@email.com" ]
then
    GIT_AUTHOR_EMAIL="new@email.com"
fi
' -- --all
```

---

## ⚠️ Warning

* Very slow
* Dangerous
* Rewrites entire history
* Not recommended now

👉 Deprecated in favor of `git filter-repo`

---

# 🔹 4. git-filter-repo.md

## 📌 What is git filter-repo?

Modern replacement for `filter-branch`.

Much:

* Faster
* Safer
* Easier

Install separately (Python tool).

---

## Example: Remove a File from History

```bash
git filter-repo --path secrets.txt --invert-paths
```

---

## Remove Large Files

```bash
git filter-repo --strip-blobs-bigger-than 10M
```

---

## ⚠️ Important

After rewriting history:

* Force push required
* Team members must reclone

---

# 🔹 5. rewriting-history.md

Rewriting history means modifying existing commits.

---

## 📌 Methods

### 1️⃣ Amend Last Commit

```bash
git commit --amend
```

---

### 2️⃣ Interactive Rebase

```bash
git rebase -i HEAD~5
```

You can:

* Reorder commits
* Squash commits
* Edit commits
* Drop commits

---

### 3️⃣ Reset

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
```

---

## ⚠️ Golden Rule

❌ Never rewrite public history
✅ Safe only before pushing

---

# 🔹 6. git-worktree.md

## 📌 What is Git Worktree?

Allows multiple working directories from the same repo.

Normally:

* One branch = one folder

With worktree:

* Multiple branches = multiple folders

---

## 📌 Example

```bash
git worktree add ../feature-branch feature
```

Creates new directory:

```
../feature-branch
```

Now you can:

* Work on two branches simultaneously
* Avoid stash

---

## 📌 List Worktrees

```bash
git worktree list
```

---

## 📌 Remove Worktree

```bash
git worktree remove <path>
```

---

## 🔥 DevOps Use Case

* Production hotfix while feature development continues
* Parallel testing

---

# 🔹 7. sparse-checkout.md

## 📌 What is Sparse Checkout?

Used when:

* Repo is huge
* You need only specific folders

Instead of cloning entire repo contents.

---

## 📌 Enable Sparse Checkout

```bash
git sparse-checkout init
git sparse-checkout set folder1 folder2
```

---

Now only those folders appear in working directory.

---

## 🔥 Use Case

Large monorepo with:

* frontend
* backend
* infra

You can checkout only `/infra`

---

# 🔹 8. shallow-clones.md

## 📌 What is Shallow Clone?

Clones repository with limited history.

---

## 📌 Clone Last 1 Commit

```bash
git clone --depth 1 <repo-url>
```

---

## 📌 Benefits

* Faster clone
* Less storage
* Useful in CI/CD pipelines

---

## 📌 Convert to Full Clone

```bash
git fetch --unshallow
```

---

## 🔥 DevOps Use Case

CI pipelines use shallow clones to:

* Speed up builds
* Reduce storage

---

# 🔹 9. large-file-storage.md

## 📌 What is Git LFS?

Git Large File Storage is used to manage large files like:

* Images
* Videos
* ML models
* Binaries

Instead of storing full file in Git:

* Git stores pointer
* Actual file stored separately

---

## 📌 Install Git LFS

```bash
git lfs install
```

---

## 📌 Track File Types

```bash
git lfs track "*.zip"
```

---

## 📌 Why Needed?

Git is optimized for:

* Text files
* Small files

Large files:

* Slow down repo
* Increase clone time
* Bloat history

---

## 🔥 DevOps / ML Use Case

* Model files
* Large datasets
* Build artifacts

---

# 🎯 Summary Table

| Topic             | Purpose                      | Used For         |
| ----------------- | ---------------------------- | ---------------- |
| reflog            | Track HEAD history           | Recovery         |
| Recover commits   | Restore lost work            | Safety           |
| filter-branch     | Rewrite history (old)        | Cleanup          |
| filter-repo       | Rewrite history (modern)     | Remove secrets   |
| rewriting history | Modify commits               | Clean commit log |
| worktree          | Multiple working directories | Parallel work    |
| sparse checkout   | Partial checkout             | Large monorepo   |
| shallow clone     | Limited history clone        | CI/CD            |
| Git LFS           | Manage large files           | ML/Media         |


