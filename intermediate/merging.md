# 🌿 Git Merging – Complete Notes

This document covers all essential concepts related to **Git merging**, including types of merges, conflicts, and conflict resolution tools. These notes are useful for **learning Git**, **revision**, and **interview preparation**.

---

## 📁 Folder Structure

merging/ │ ├── git-merge.md ├── fast-forward-merge.md ├── three-way-merge.md ├── merge-conflicts.md ├── resolving-conflicts.md └── merge-tools.md

---

## 📄 git-merge.md
### 🔹 What is Git Merge?
`git merge` is a command used to combine changes from one branch into another branch.

---

### 🔹 Key Features
- Integrates changes from multiple branches
- Maintains commit history
- Can create a merge commit
- Commonly used to merge feature branches into `main` or `master`

---

### 🔹 Syntax
```bash
git merge <branch-name>


---

🔹 Use Case

Collaborative development

Integrating completed features



---

📄 fast-forward-merge.md

🔹 What is Fast-Forward Merge?

A fast-forward merge occurs when the current branch has no new commits since the target branch was created.


---

🔹 Characteristics

No merge commit is created

Branch pointer simply moves forward

Linear and clean history



---

🔹 Example

git checkout main
git merge feature-branch


---

🔹 Advantages

Simple commit history

Easy to understand



---

🔹 Disadvantages

Does not show feature branch history clearly



---

📄 three-way-merge.md

🔹 What is Three-Way Merge?

A three-way merge happens when both branches have diverged and contain unique commits.


---

🔹 Involves

Common ancestor commit

Latest commit of source branch

Latest commit of target branch



---

🔹 Result

Git creates a new merge commit



---

🔹 Example

git merge feature-branch


---

🔹 Visual Representation

A---B---C (main)
     \
      D---E (feature)


---

🔹 Advantages

Preserves full branch history

Better for tracking changes



---

📄 merge-conflicts.md

🔹 What is a Merge Conflict?

A merge conflict occurs when Git cannot automatically merge changes.


---

🔹 Common Causes

Same file modified in multiple branches

Same line edited differently



---

🔹 Git Conflict Message

CONFLICT (content): Merge conflict in file.txt


---

🔹 Conflict Markers

<<<<<<< HEAD
Your changes
=======
Incoming changes
>>>>>>> feature-branch


---

🔹 Important Note

Git pauses the merge until conflicts are resolved



---

📄 resolving-conflicts.md

🔹 Steps to Resolve Merge Conflicts

1. Open the conflicted file


2. Identify conflict markers


3. Decide which changes to keep


4. Remove conflict markers


5. Save the file


6. Stage the resolved file


7. Complete the merge




---

🔹 Commands

git add file.txt
git commit


---

🔹 Abort a Merge

git merge --abort


---

📄 merge-tools.md

🔹 What are Merge Tools?

Merge tools help resolve conflicts using a visual interface.


---

🔹 Popular Merge Tools

vimdiff

meld

kdiff3

VS Code



---

🔹 Configure Merge Tool

git config --global merge.tool meld


---

🔹 Launch Merge Tool

git mergetool


---

🔹 Benefits

Visual comparison

Faster conflict resolution

Reduced errors



---

✅ Quick Summary

Fast-forward merge → No new commit

Three-way merge → Creates merge commit

Merge conflict → Manual resolution required

Merge tools → Simplify conflict handling



---

