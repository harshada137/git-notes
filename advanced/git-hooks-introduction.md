## 📁 1️⃣ git-hooks-introduction.md

### What it covers:

* What are Git Hooks?
* Why they are used?
* Where they are located (`.git/hooks/`)
* How they work

### Simple Meaning:

Git hooks are **scripts that run automatically before or after Git actions** like commit, push, merge, etc.

Example:

* Before commit → run tests
* Before push → check code quality

---

## 📁 2️⃣ client-side-hooks.md

### What it covers:

Hooks that run **on developer’s local machine**.

### Common Client Hooks:

* `pre-commit`
* `commit-msg`
* `pre-push`
* `post-commit`

### Use Cases:

* Check code formatting
* Run ESLint
* Prevent committing secrets
* Enforce commit message format

👉 These hooks affect only your local repo unless shared via tools.

---

## 📁 3️⃣ server-side-hooks.md

### What it covers:

Hooks that run **on remote Git server** (like GitHub Enterprise, GitLab, Bitbucket).

### Common Server Hooks:

* `pre-receive`
* `update`
* `post-receive`

### Use Cases:

* Block direct push to main branch
* Enforce branch protection rules
* Trigger CI/CD pipelines

👉 Used more in team/production environments.

---

## 📁 4️⃣ pre-commit-hooks.md

### What it covers:

Hook that runs **before commit is created**.

### When it runs:

```
git commit
```

Before commit is finalized.

### Use Cases:

* Run tests
* Run linters
* Check formatting
* Prevent committing large files

If script fails → ❌ commit is cancelled.

Example:

```bash
npm run lint
```

---

## 📁 5️⃣ commit-msg-hooks.md

### What it covers:

Hook that checks the **commit message**.

### Use Cases:

* Enforce commit format:

  ```
  feat: add login API
  fix: resolve docker bug
  ```
* Prevent empty messages
* Enforce ticket IDs

If format is wrong → commit rejected.

Very useful in DevOps teams.

---

## 📁 6️⃣ pre-push-hooks.md

### What it covers:

Hook that runs **before pushing to remote**.

### When it runs:

```
git push
```

### Use Cases:

* Run tests before pushing
* Prevent pushing to protected branches
* Check for sensitive data

If script fails → ❌ push blocked.

---

## 📁 7️⃣ hook-frameworks.md

### What it covers:

Tools that make managing hooks easier.

Because `.git/hooks` are not shared by default.

### Popular Hook Tools:

* **Husky**

  * Used in JavaScript projects
  * Integrates with npm
  * Very common in MERN projects

* **lint-staged**

  * Runs linters only on staged files
  * Used with Husky

* **pre-commit**

  * Multi-language hook framework
  * Popular in Python projects

---

# 🔥 Why This Folder Is Important (For DevOps & Interviews)

Since you're preparing for DevOps roles, this section is important because:

* Ensures code quality before CI/CD
* Automates validation
* Prevents production issues
* Enforces team standards

---

# 🎯 Interview Example Question

**Q: How can you prevent developers from pushing broken code?**

Answer:

* Use `pre-commit` and `pre-push` hooks
* Run tests automatically
* Enforce commit message rules
* Use Husky to share hooks across team

