# 📂 06 – Advanced Collaboration

## 1️⃣ code-review-advanced.md

### Code Review (Advanced)

* Ensures code quality before merging
* Involves automated checks + peer reviews
* Best practices:

  * Review small, focused PRs
  * Comment on logic, readability, and standards
  * Approve only after tests pass

Benefits:

* Catch bugs early
* Share knowledge among team members
* Maintain code consistency

---

## 2️⃣ pull-request-templates.md

### Pull Request Templates

* Standardize PR descriptions
* Helps reviewers understand changes
* Can include:

  * Summary of changes
  * Related issues
  * Testing steps
  * Reviewer checklist

Example template:

```
### Summary
### Issue Reference
### Testing Steps
### Checklist
- [ ] Code compiles
- [ ] Tests pass
```

Benefits:

* Faster, consistent reviews
* Avoid missing important context
* Improves collaboration

---

## 3️⃣ branch-protection-rules.md

### Branch Protection Rules

* Prevent direct pushes to main/master
* Enforce:

  * Required reviews
  * Passing CI checks
  * Status checks before merge
* Optional:

  * Restrict who can push
  * Require signed commits

Benefits:

* Keeps main branch stable
* Reduces accidental overwrites
* Enforces process discipline

---

## 4️⃣ required-reviews.md

### Required Reviews

* Ensures PRs are approved before merge
* Can specify:

  * Number of required reviewers
  * Who can approve
* Works with branch protection rules

Benefits:

* Prevents unreviewed code from being merged
* Promotes accountability

---

## 5️⃣ codeowners-file.md

### CODEOWNERS File

* Defines responsible team/people for files or folders
* GitHub auto-requests reviews from owners on PRs
* Example:

```
# All files in src/
src/ @frontend-team
# Config files
config/ @devops-team
```

Benefits:

* Automatically assigns reviewers
* Ensures critical files are always reviewed
* Helps manage large projects

---

## 6️⃣ team-management.md

### Team Management

* Organize members into teams in GitHub
* Assign roles:

  * Admin
  * Maintainer
  * Member
* Benefits:

  * Control repo access
  * Easier management of permissions
  * Streamlines collaboration

---

# 🎯 Summary – Advanced Collaboration Topics

| Topic                   | Purpose                                    |
| ----------------------- | ------------------------------------------ |
| Code Review Advanced    | Improve code quality and knowledge sharing |
| Pull Request Templates  | Standardize PRs and make reviews efficient |
| Branch Protection Rules | Keep main branch safe and stable           |
| Required Reviews        | Enforce review discipline before merging   |
| CODEOWNERS File         | Auto-assign reviewers for critical files   |
| Team Management         | Organize access & permissions efficiently  |

