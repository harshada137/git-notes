# 📁 07 – Exercises (Hands-on Practice)

These exercises are designed to:

* Strengthen branching skills
* Handle merge conflicts
* Create pull requests
* Work in team collaboration scenarios

---

# 1️⃣ `exercise-01-branching-merging.md`

## 🎯 Objective:

Learn how to create branches, work independently, and merge changes safely.

---

## 🔹 Why Branching is Important?

In real companies:

* `main` branch = production code
* Developers never work directly on `main`
* They create feature branches

Example:

```
main
   └── feature-login
   └── feature-payment
   └── bugfix-header
```

---

## 🔹 What This Exercise Teaches

### Step 1: Create a branch

```bash
git branch feature-xyz
git checkout feature-xyz
```

or

```bash
git checkout -b feature-xyz
```

### Step 2: Make changes

Edit file → Add → Commit

```bash
git add .
git commit -m "Added feature xyz"
```

### Step 3: Merge into main

```bash
git checkout main
git merge feature-xyz
```

---

## 🔹 What You Learn

* Branch isolation
* Clean workflow
* Fast-forward merge
* Non-fast-forward merge

---

## 🔹 Real DevOps Use Case

When working on CI/CD pipelines:

* You create a branch
* Modify pipeline file
* Test
* Merge after approval

---

# 2️⃣ `exercise-02-conflict-resolution.md`

## 🎯 Objective:

Learn how to handle merge conflicts like a professional.

---

## 🔹 What is a Merge Conflict?

It happens when:
Two branches modify the same line of the same file.

Example:

Branch A:

```python
print("Hello World")
```

Branch B:

```python
print("Hello DevOps")
```

Git doesn’t know which one to keep.

---

## 🔹 What Git Shows During Conflict

```text
<<<<<<< HEAD
print("Hello World")
=======
print("Hello DevOps")
>>>>>>> feature-branch
```

You must manually edit and choose the correct version.

---

## 🔹 Steps to Resolve

1. Open conflicting file
2. Remove conflict markers
3. Keep correct code
4. Stage file

   ```bash
   git add file.py
   ```
5. Commit merge

   ```bash
   git commit
   ```

---

## 🔹 What You Learn

* Conflict detection
* Manual resolution
* Understanding Git markers
* Safe merging practices

---

## 🔹 Interview Importance

You might be asked:

> “What steps will you take if merge conflict occurs in production branch?”

Now you know the answer clearly.

---

# 3️⃣ `exercise-03-first-pull-request.md`

## 🎯 Objective:

Create your first Pull Request (PR).

---

## 🔹 What is a Pull Request?

A Pull Request is:

> A request to merge your branch into another branch.

PRs are core to team collaboration on **GitHub**.

---

## 🔹 Steps in This Exercise

1. Create branch
2. Make changes
3. Push to GitHub

   ```bash
   git push origin feature-branch
   ```
4. Go to GitHub
5. Click "Compare & Pull Request"
6. Add title & description
7. Create PR

---

## 🔹 What You Learn

* Remote repository interaction
* Branch comparison
* Commit history review
* Professional PR description writing

---

## 🔹 Real DevOps Scenario

If you're modifying:

* Terraform file
* Jenkinsfile
* Dockerfile
* Kubernetes YAML

You MUST create PR before merging.

---

# 4️⃣ `exercise-04-collaboration.md`

## 🎯 Objective:

Simulate team-based development.

This exercise connects everything together.

---

## 🔹 What It Covers

* Multiple developers working
* Creating issues
* Assigning tasks
* Branch creation
* Pull requests
* Code review
* Merge
* Closing issue

---

## 🔹 Example Workflow Simulation

1. Issue created: "Add login feature"
2. Assigned to Developer A
3. Developer A creates branch
4. Developer A pushes changes
5. Creates Pull Request
6. Developer B reviews
7. Comments on code
8. Changes updated
9. PR approved
10. Merged into main
11. Issue closed

---

## 🔹 What You Learn

* Professional Git workflow
* Team coordination
* Review culture
* Clean history management
* Communication in development

---

# 🔥 How All 4 Exercises Connect

| Exercise            | Skill Developed           |
| ------------------- | ------------------------- |
| Branching & Merging | Safe development workflow |
| Conflict Resolution | Handling real problems    |
| First Pull Request  | Remote collaboration      |
| Collaboration       | Complete team workflow    |

---

# 🚀 Why This Is Important for You (DevOps)

Since you are preparing for DevOps:

You will:

* Review PRs
* Manage infrastructure code
* Handle conflicts
* Maintain main branch
* Work with multiple developers
* Protect production code

In CI/CD environments, improper merging can break pipelines.

These exercises build confidence for:

* Git interviews
* Real company workflow
* Production handling

---
