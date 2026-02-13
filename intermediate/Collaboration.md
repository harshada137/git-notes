# 📁 06 – Collaboration (Git & GitHub Team Workflow)

Collaboration means **multiple developers working on the same project without breaking each other’s work**.

It mainly happens on platforms like **GitHub** using **Git**.

---

# 1️⃣ `forking-repositories.md`

## 🔹 What is Forking?

Forking means:

> Creating your own copy of someone else’s repository into your GitHub account.

It is commonly used in:

* Open-source contributions
* When you don’t have direct write access to a repo

### 📌 How it works:

1. Original repository (owned by someone else)
2. You click **Fork**
3. GitHub creates:

   ```
   original-repo  →  your-copy-of-repo
   ```
4. You clone your fork locally
5. Make changes
6. Push changes
7. Create Pull Request

### 🔹 Fork vs Clone

| Fork                    | Clone                    |
| ----------------------- | ------------------------ |
| Happens on GitHub       | Happens on local machine |
| Creates new remote repo | Downloads repo locally   |

### 🔹 Real-world Example

If you want to contribute to **Kubernetes**, you must fork the repository first.

---

# 2️⃣ `pull-requests.md`

## 🔹 What is a Pull Request (PR)?

A Pull Request is:

> A request to merge your changes into another branch or repository.

It is how collaboration happens.

### 🔹 PR Workflow

1. Create feature branch
2. Make changes
3. Push branch
4. Create Pull Request
5. Team reviews
6. Merge

### 🔹 What PR includes:

* Title
* Description
* List of commits
* Code differences (diff view)
* Review comments

### 🔹 Why PR is important?

* Enables code review
* Prevents breaking production
* Maintains code quality
* Required in professional DevOps workflow

---

# 3️⃣ `code-review-basics.md`

## 🔹 What is Code Review?

Code review is:

> The process where team members check your code before merging.

It ensures:

* Clean code
* No bugs
* Security checks
* Standard formatting
* Best practices

### 🔹 What reviewers check:

* Logic correctness
* Naming conventions
* Performance issues
* Security vulnerabilities
* Test coverage

### 🔹 Approval Flow

1. Developer raises PR
2. Reviewer comments
3. Developer fixes issues
4. Reviewer approves
5. Merge

In companies, this is mandatory.

---

# 4️⃣ `github-issues.md`

## 🔹 What are Issues?

Issues are:

> Task trackers or bug reports inside a GitHub repository.

They are used for:

* Bug tracking
* Feature requests
* Documentation improvements
* Planning work

### 🔹 Issue contains:

* Title
* Description
* Labels
* Assignee
* Milestone
* Comments

Example:

```
Title: Fix login bug
Label: bug
Assignee: Harshada
```

### 🔹 Why important?

In DevOps and Agile teams:

* Work is tracked using Issues
* Each issue can be linked to a PR
* Helps in sprint planning

---

# 5️⃣ `issue-templates.md`

## 🔹 What are Issue Templates?

Issue Templates are:

> Predefined formats for creating issues.

Instead of random bug reports, teams create structured forms like:

```
Bug Title:
Steps to Reproduce:
Expected Behavior:
Actual Behavior:
Screenshots:
```

### 🔹 Why needed?

* Maintains consistency
* Saves time
* Reduces confusion
* Makes debugging easier

Templates are stored inside:

```
.github/ISSUE_TEMPLATE/
```

---

# 6️⃣ `collaborator-management.md`

## 🔹 What is Collaborator Management?

This is about:

> Managing who can access and modify your repository.

### 🔹 Types of Access in GitHub:

* Read
* Triage
* Write
* Maintain
* Admin

### 🔹 What Admin Can Do:

* Add/remove collaborators
* Change settings
* Delete repo
* Manage secrets
* Manage branches

### 🔹 In Organizations

Companies use:

* Teams
* Role-based access
* Branch protection rules

Example:

* Only senior devs can merge to `main`
* Junior devs can create branches only

---

# 🔥 How All These Connect Together

Here’s a full collaboration cycle:

1. Issue is created
2. Developer forks repo (if open-source)
3. Creates feature branch
4. Solves issue
5. Raises Pull Request
6. Code review happens
7. Changes merged
8. Issue closed

This is professional workflow used in:

* DevOps teams
* Cloud projects
* Open-source
* Corporate development
]
