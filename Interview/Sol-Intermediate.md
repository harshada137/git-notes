
# Level 2: Intermediate Git Practical – Solutions and Explanation


## 1. Create a new branch called `feature-login` and switch to it.

### Solution
```bash
git checkout -b feature-login
````

### Explanation

* `git checkout -b` creates a new branch and switches to it in one step.
* `feature-login` is typically used for developing a specific feature separately from the main code.

---

## 2. Create a new file named `login.txt`, add some content, and commit the changes.

### Solution

```bash
echo "Login feature code" > login.txt
git add login.txt
git commit -m "Added login feature file"
```

### Explanation

* `echo` creates the file and adds content.
* `git add` moves the file to the **staging area**.
* `git commit` permanently records the change in the repository.

---

## 3. Switch back to the `main` branch.

### Solution

```bash
git checkout main
```

### Explanation

* `git checkout main` changes the working branch to **main**.
* Any new work will now happen on the main branch.

---

## 4. Merge the `feature-login` branch into the `main` branch.

### Solution

```bash
git merge feature-login
```

### Explanation

* `git merge` combines the changes from `feature-login` into the current branch (`main`).
* This is commonly done after completing a feature.

---

## 5. View the list of all branches in the repository.

### Solution

```bash
git branch
```

### Explanation

* Displays all local branches.
* The current branch is marked with `*`.

Example:

```
* main
  feature-login
```

---

## 6. Delete the branch `feature-login` after merging.

### Solution

```bash
git branch -d feature-login
```

### Explanation

* `-d` deletes the branch **only if it has been merged**.
* This keeps the repository clean by removing unused branches.

---

## 7. Temporarily save changes using Git stash.

### Solution

```bash
git stash
```

### Explanation

* `git stash` saves uncommitted changes temporarily.
* It allows you to switch branches without committing incomplete work.

---

## 8. View the stash list and apply the latest stash.

### Solution

```bash
git stash list
git stash apply
```

### Explanation

* `git stash list` shows all saved stashes.
* `git stash apply` restores the most recent stash.

Example:

```
stash@{0}: WIP on main
```

---

## 9. Add a remote repository.

### Solution

```bash
git remote add origin https://github.com/username/repository.git
git remote -v
```

### Explanation

* `git remote add origin` connects the local repository to a remote repository.
* `git remote -v` verifies the remote repository link.

---

## 10. Push the `main` branch to the remote repository.

### Solution

```bash
git push -u origin main
```

### Explanation

* `git push` uploads local commits to the remote repository.
* `-u` sets the **upstream branch**, so future pushes can be done using just `git push`.

---

## 11. Compare the difference between two commits.

### Solution

```bash
git diff commit_id1 commit_id2
```

### Explanation

* Shows the changes between two commits.
* Useful for reviewing what changed between versions.

Example:

```
git diff a1b2c3d d4e5f6g
```

---

## 12. View commit history in one-line format.

### Solution

```bash
git log --oneline
```

### Explanation

* Displays commit history in a compact format.
* Each commit appears in a single line.

Example:

```
a3f5b21 Added login feature
b7c9d10 Initial commit
```

---
