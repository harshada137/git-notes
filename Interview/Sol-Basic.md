# Level 1: Basic Git Practical – Solutions & Explanation


## Task 1: Initialize a Git repository in a new project folder

### Solution
```bash
mkdir project
cd project
git init
git status
````

### Explanation

* `mkdir project` creates a new directory.
* `cd project` moves into that directory.
* `git init` initializes a new Git repository.
* `git status` shows the current repository status.

---

## Task 2: Create a file `hello.txt`, add content, and commit it

### Solution

```bash
echo "Hello Git" > hello.txt
git add hello.txt
git commit -m "Initial commit"
```

### Explanation

* `echo` creates the file and adds content.
* `git add` stages the file.
* `git commit` saves the change to the repository history.

---

## Task 3: Check the commit history

### Solution

```bash
git log
git log --oneline
```

### Explanation

* `git log` shows detailed commit history.
* `git log --oneline` shows a compact version.

---

## Task 4: Rename the branch `master` to `main`

### Solution

```bash
git branch -m master main
```

### Explanation

* `-m` renames the branch from `master` to `main`.

---

## Task 5: Configure Git username and email globally

### Solution

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Explanation

* These settings attach your identity to commits.
* `--global` applies to all repositories on your system.

---

## Task 6: Check the difference between staged and unstaged changes

### Solution

```bash
git status
git diff
git diff --staged
```

### Explanation

* `git status` shows file states.
* `git diff` shows unstaged changes.
* `git diff --staged` shows staged changes.

---

## Task 7: Remove a file from tracking but keep it locally

### Solution

```bash
git rm --cached filename.txt
```

### Explanation
```
* Removes the file from Git tracking.
* The file remains in the local directory.

```
