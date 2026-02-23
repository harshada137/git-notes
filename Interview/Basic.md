## 🔹 Basic Git Questions
### 1️⃣ What is Git?

**Version Control** is a system that records changes to files over time so you can recall specific versions later. It lets multiple developers collaborate without overwriting each other's work.

**Distributed VCS (DVCS)** means every developer has a complete copy of the entire repository history on their local machine — not just the latest snapshot. Git is a DVCS, which means:
- You can work offline and commit locally
- No single point of failure (unlike centralized VCS like SVN)
- Operations like log, diff, and commit are extremely fast since they run locally

Git was created by Linus Torvalds in 2005 to manage the Linux kernel source code.

---

### 2️⃣ What is the difference between Git and GitHub?

**Git** is the version control tool itself — it runs locally on your machine as a command-line tool and tracks changes in your code.

**GitHub** is a cloud-based hosting platform built around Git. It provides a web interface, collaboration features, pull requests, issue tracking, CI/CD via GitHub Actions, and remote repository storage. Think of Git as the engine and GitHub as the car built around it.

Other alternatives to GitHub include GitLab and Bitbucket — they all use Git underneath.

---

### 3️⃣ What is a Repository in Git?

A repository (repo) is a directory that Git tracks. It contains all your project files along with the entire history of every change ever made. Internally, Git stores this history in a hidden `.git` folder at the root of the project.

There are two types:
- **Local repository** — exists on your machine
- **Remote repository** — hosted on a server (like GitHub), shared with the team

You create one with `git init` or clone an existing one with `git clone <url>`.

---

### 4️⃣ What is the difference between `git pull` and `git fetch`?

Both commands download changes from a remote repository, but they differ in what they do next.

`git fetch` only downloads the changes from the remote and stores them in your local remote-tracking branches (like `origin/main`). It does **not** modify your working directory or current branch. You can then inspect the changes before integrating them.

`git pull` is essentially `git fetch` followed by `git merge`. It downloads the remote changes and immediately merges them into your current branch.

In practice, `git fetch` is safer because it lets you review changes before merging. `git pull` is faster for routine updates when you trust the remote.

---

### 5️⃣ What is the difference between `git merge` and `git rebase`?

Both integrate changes from one branch into another but they do it differently.

**`git merge`** creates a new "merge commit" that ties together the histories of both branches. The original branch histories are preserved exactly as they happened. This is safe and non-destructive but can result in a messy, non-linear history with lots of merge commits.

**`git rebase`** moves or replays your commits on top of another branch, rewriting commit history to appear linear. The result looks like development happened in a straight line, making the history much cleaner. However, it rewrites commit hashes, so you should **never rebase commits that have been pushed to a shared remote branch**, as it will cause problems for other developers.

Rule of thumb: use `merge` for shared/public branches, use `rebase` for cleaning up local feature branch history before merging.

---

### 6️⃣ What are the three stages in Git?

Git has three main areas that files pass through:

**Working Directory** — this is where you actively edit files. Changes here are "untracked" or "modified" but Git isn't recording them yet.

**Staging Area (Index)** — when you run `git add <file>`, you move changes to the staging area. This is a preparation zone where you decide exactly which changes will go into your next commit. You can stage some files and leave others out.

**Repository (Local Repo)** — when you run `git commit`, the staged changes are permanently saved as a snapshot in your local Git history. This is the `.git` folder on disk.

The flow is: Working Directory → `git add` → Staging Area → `git commit` → Repository

---

### 7️⃣ What is a Commit in Git?

A commit is a snapshot of your staged changes saved permanently in Git's history. Each commit has:
- A unique SHA-1 hash (e.g., `a3f5c1d`) used to identify it
- Author name and email
- A timestamp
- A commit message describing the change
- A pointer to its parent commit(s)

Commits form a linked chain, which is how Git builds the full history of a project. A good commit should be atomic (one logical change), and its message should clearly describe what and why.

```bash
git commit -m "Add user authentication feature"
```

---

### 8️⃣ How do you create a new branch?

A branch in Git is just a lightweight, movable pointer to a specific commit. Creating a branch doesn't copy files — it just creates a new pointer.

```bash
# Create a branch
git branch feature/login

# Create and switch to it in one step (recommended)
git checkout -b feature/login

# Modern syntax (Git 2.23+)
git switch -c feature/login
```

Branches allow you to work on features or bug fixes in isolation without affecting the main codebase.

---

### 9️⃣ How do you switch between branches?

```bash
# Classic way
git checkout branch-name

# Modern way (Git 2.23+)
git switch branch-name
```

Before switching, make sure your working directory is clean (no uncommitted changes), or Git will either block the switch or carry those changes into the new branch. You can use `git stash` to temporarily save uncommitted work before switching.

---

### 🔟 What is a Merge Conflict and how do you resolve it?

A **merge conflict** occurs when two branches have modified the same part of the same file and Git can't automatically decide which version to keep. Git pauses the merge and asks you to resolve it manually.

Git marks the conflict in the file like this:

```
<<<<<<< HEAD
This is my version of the code
=======
This is the incoming branch's version
>>>>>>> feature/login
```

**Steps to resolve:**

1. Open the conflicted file and decide which version to keep (or combine both)
2. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
3. Stage the resolved file: `git add <filename>`
4. Complete the merge: `git commit`

Tools like VS Code, IntelliJ, or `git mergetool` provide a visual 3-way diff to make this easier.

---

## 🔹 Basic GitHub Questions

---

### 1️⃣1️⃣ What is GitHub?

GitHub is a web-based platform for hosting Git repositories. It adds collaboration features on top of Git including pull requests, code reviews, issue tracking, project boards, wikis, and GitHub Actions for CI/CD. It is owned by Microsoft and is the world's largest source code hosting platform with over 100 million developers.

---

### 1️⃣2️⃣ What is a Pull Request (PR)?

A Pull Request is a GitHub feature that lets you notify team members that you've pushed changes to a branch and would like them reviewed before merging into the main branch. It's the core of collaborative development on GitHub.

A PR includes:
- A diff showing exactly what changed
- A space for discussion and code review comments
- The ability for reviewers to request changes or approve
- CI/CD status checks
- A merge button once approved

The workflow is typically: create branch → push changes → open PR → get review → merge.

---

### 1️⃣3️⃣ What is a Fork in GitHub?

A fork is a personal copy of someone else's repository that lives in your own GitHub account. It's used when you want to contribute to a project you don't have write access to (common in open source).

The workflow is: Fork the repo → clone your fork locally → make changes → push to your fork → open a Pull Request back to the original repo.

A fork is different from a branch — a branch is within the same repository, while a fork is a completely separate copy under your account.

---

### 1️⃣4️⃣ What is GitHub Actions?

GitHub Actions is a built-in CI/CD (Continuous Integration/Continuous Deployment) platform on GitHub. It lets you automate workflows directly in your repository using YAML configuration files stored in `.github/workflows/`.

Common use cases include automatically running tests on every push, building and deploying applications, code linting, generating release notes, and sending notifications.

A basic example that runs tests on every push:

```yaml
name: Run Tests
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm test
```

---

### 1️⃣5️⃣ What is the difference between Public and Private Repositories?

A **public repository** is visible to anyone on the internet. Anyone can view and clone the code, though only collaborators with permission can push changes. Public repos are used for open source projects and portfolios.

A **private repository** is only visible to you and the collaborators you explicitly invite. No one else can see or clone it. Private repos are used for proprietary code, client work, and anything you don't want publicly exposed.

On GitHub, both public and private repos are free for individuals. Organizations may have additional access control features depending on their plan. GitHub Actions minutes and storage limits also differ between the two.
