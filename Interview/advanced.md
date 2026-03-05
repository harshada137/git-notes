
### 1️⃣ Explain `git reflog` in recovery scenarios with an example.

**Answer:**
`git reflog` records every movement of HEAD, even those not in the branch history.

**Example:**
If you accidentally run:

```bash
git reset --hard HEAD~3
```

You can recover the lost commit:

```bash
git reflog
git checkout <lost-commit-id>
git branch recovered-branch
```

**Use case:** Recover commits after accidental reset or force push.

---

### 2️⃣ How does Git handle large repositories efficiently?

**Answer:**

* Uses **packfiles**: stores objects in compressed binary files.
* **Delta compression**: only stores differences between similar files.
* **Git LFS**: replaces large files with lightweight pointers.

**Commands:**

```bash
git gc            # Garbage collection
git repack -a -d  # Repack objects
```

---

### 3️⃣ What is a **detached HEAD** and how do you safely work with it?

**Answer:**
A detached HEAD occurs when you check out a commit instead of a branch:

```bash
git checkout <commit-id>
```

* You can make experimental changes.
* If you commit, it’s **not on any branch**.

**Safe approach:**

```bash
git checkout -b new-feature
```

Now commits are attached to a branch.

---

### 4️⃣ Difference between **hard reset, soft reset, and mixed reset**.

| Reset Type | Command Example            | Effect                           |
| ---------- | -------------------------- | -------------------------------- |
| Soft       | `git reset --soft HEAD~1`  | Moves HEAD, keeps changes staged |
| Mixed      | `git reset --mixed HEAD~1` | Moves HEAD, unstages changes     |
| Hard       | `git reset --hard HEAD~1`  | Moves HEAD, discards all changes |

**Use case:** Choosing based on whether you want to keep uncommitted changes or remove them completely.

---

### 5️⃣ Explain `git bisect` for debugging production issues.

**Answer:**
`git bisect` performs a **binary search** to find the commit that introduced a bug.

**Steps:**

```bash
git bisect start
git bisect bad       # current commit has bug
git bisect good <commit-id> # known good commit
```

Git checks out the middle commit. Mark as `good` or `bad` until the culprit commit is found.

**Use case:** Pinpointing regressions quickly in large histories.

---

### 6️⃣ What is **git cherry-pick** and when should it be used?

**Answer:**
`git cherry-pick <commit>` applies a specific commit from another branch.

**Use case:**

* Apply bug fix to `main` without merging the entire feature branch.
* Backporting features to older release branches.

```bash
git checkout main
git cherry-pick <commit-id>
```

---

### 7️⃣ Explain **submodules** and their challenges.

**Answer:**
Submodules allow a repository to include another repository as a dependency.

```bash
git submodule add <repo-url> path/
git submodule update --init --recursive
```

**Challenges:**

* Requires manual updating in parent repo.
* CI/CD pipelines need recursive cloning.
* Complex version management.

---

### 8️⃣ How does Git handle **merge conflicts internally**?

**Answer:**

* Git uses a **3-way merge**: base, local, remote.
* Conflict occurs if **same lines modified** in both branches.
* Conflicts are marked in files:

```text
<<<<<<< HEAD
local change
=======
incoming change
>>>>>>> branch
```

**Resolution:**

* Edit manually, add, commit.
* Use `git merge --strategy-option=theirs/ours` in special cases.

---

### 9️⃣ Explain **reflog + reset recovery after a force push.**

**Scenario:** Teammate accidentally force-pushed to `main`.

**Solution:**

```bash
git reflog
git checkout <commit-id-before-force-push>
git branch recover-main
git push origin recover-main
```

Ensures the original history is restored without losing commits.

---

### 🔟 How does **Git store objects internally**?

**Answer:**
Git is **content-addressable**. It stores:

* **Blob:** file content
* **Tree:** directory structure
* **Commit:** points to tree + metadata
* **Tag:** named pointer to commit

Objects are hashed using **SHA-1/SHA-256** and stored in `.git/objects/`.

**Example:**

```bash
ls .git/objects/
```

---

### 1️⃣1️⃣ Explain **force push safely** using `--force-with-lease`.

**Answer:**
`--force-with-lease` ensures you **don’t overwrite others’ commits**:

```bash
git push --force-with-lease origin main
```

* Safer than `--force` in shared branches.
* Only allows force push if remote HEAD matches what you expect.

---

### 1️⃣2️⃣ What are **rebase interactive and squash commits**?

**Answer:**

```bash
git rebase -i HEAD~5
```

* Allows you to **reorder, squash, edit, or remove commits**.
* Squashing merges multiple commits into one for clean history.

**Use case:** Feature branch cleanup before merging.

---

### 1️⃣3️⃣ How does Git handle **binary files differently from text**?

* Binary files cannot be **diffed** effectively.
* Stored as **full object snapshots** instead of line diffs.
* Use **Git LFS** for large binaries to avoid repo bloat.

---

### 1️⃣4️⃣ Explain **Git Hooks** with advanced use cases.

Stored in `.git/hooks/`. Examples:

| Hook       | Use case                             |
| ---------- | ------------------------------------ |
| pre-commit | Lint code before commit              |
| pre-push   | Run tests before push                |
| post-merge | Auto-update dependencies after merge |

**Advanced scenario:** Enforce commit message format for CI/CD pipelines.

---

### 1️⃣5️⃣ Explain **advanced branching strategy for production**.

**GitFlow / Production-ready workflow:**

1. `main` → stable production code
2. `develop` → integration branch
3. `feature/*` → feature development
4. `release/*` → pre-release testing
5. `hotfix/*` → urgent fixes on production

Merge strategy:

* Feature → Develop → PR
* Release → Main → Tag → Deploy
* Hotfix → Main → Tag → Merge back to Develop
