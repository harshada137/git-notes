# Git Branching

## What Are Branches?

Branches in Git are lightweight, movable pointers to commits. They allow you to diverge from the main line of development and work on different features, fixes, or experiments independently without affecting the main codebase.

### Key Concepts

- **Branch as a Pointer**: A branch is simply a pointer to a specific commit in your repository's history
- **HEAD**: A special pointer that indicates which branch you're currently on
- **Default Branch**: Typically `main` or `master`, representing the primary line of development
- **Isolation**: Changes in one branch don't affect other branches until merged

### Why Use Branches?

- **Parallel Development**: Multiple team members can work on different features simultaneously
- **Safe Experimentation**: Try new ideas without risking the stable codebase
- **Organized Workflow**: Keep features, bug fixes, and experiments separate
- **Code Review**: Branches facilitate pull request workflows for code review
- **Release Management**: Maintain different versions of your software

## Git Branch Command

The `git branch` command is used to create, list, rename, and delete branches.

### Listing Branches

```bash
# List all local branches
git branch

# List all branches (local and remote)
git branch -a

# List remote branches only
git branch -r

# List branches with additional information (last commit)
git branch -v

# List branches with tracking information
git branch -vv
```

### Creating Branches

```bash
# Create a new branch
git branch feature-login

# Create a branch from a specific commit
git branch feature-name <commit-hash>

# Create a branch from another branch
git branch new-branch existing-branch
```

### Deleting Branches

```bash
# Delete a branch (safe - prevents deletion of unmerged branches)
git branch -d branch-name

# Force delete a branch (even if unmerged)
git branch -D branch-name

# Delete a remote branch
git push origin --delete branch-name
```

### Renaming Branches

```bash
# Rename the current branch
git branch -m new-name

# Rename a different branch
git branch -m old-name new-name
```

### Other Useful Options

```bash
# Show merged branches
git branch --merged

# Show unmerged branches
git branch --no-merged

# Create and switch to a new branch (combines branch + checkout)
git branch feature-name && git checkout feature-name
```

## Git Checkout Command

The `git checkout` command is traditionally used to switch between branches and restore files. It's a multi-purpose command that has been partially replaced by `git switch` and `git restore` in newer Git versions.

### Switching Branches

```bash
# Switch to an existing branch
git checkout branch-name

# Create and switch to a new branch
git checkout -b new-branch-name

# Create a new branch from a specific commit
git checkout -b new-branch <commit-hash>

# Create a new branch from a remote branch
git checkout -b local-branch origin/remote-branch
```

### Restoring Files

```bash
# Discard changes in working directory
git checkout -- filename

# Restore a file from a specific commit
git checkout <commit-hash> -- filename

# Restore all files to match the last commit
git checkout -- .
```

### Detached HEAD State

```bash
# Checkout a specific commit (enters detached HEAD state)
git checkout <commit-hash>

# Checkout a specific tag
git checkout v1.0.0

# Return to a branch from detached HEAD
git checkout branch-name
```

### Common Use Cases

```bash
# Switch back to the previous branch
git checkout -

# Checkout a remote branch for the first time
git checkout --track origin/feature-branch
```

## Git Switch Command

Introduced in Git 2.23, `git switch` is a clearer, more focused command for switching branches. It removes the ambiguity of `git checkout` by handling only branch operations.

### Basic Usage

```bash
# Switch to an existing branch
git switch branch-name

# Switch to the previous branch
git switch -

# Create and switch to a new branch
git switch -c new-branch-name
git switch --create new-branch-name
```

### Creating Branches

```bash
# Create a new branch from current HEAD
git switch -c feature-auth

# Create a new branch from a specific starting point
git switch -c new-branch origin/main

# Force create a branch (reset if it exists)
git switch -C branch-name
```

### Working with Remote Branches

```bash
# Create and switch to a branch tracking a remote branch
git switch -c local-name origin/remote-branch

# Switch to a remote branch (Git automatically creates a local tracking branch)
git switch remote-branch-name
```

### Additional Options

```bash
# Discard local changes when switching
git switch -f branch-name
git switch --discard-changes branch-name

# Detach HEAD at a specific commit
git switch --detach <commit-hash>

# Switch with merge (carry over uncommitted changes)
git switch -m branch-name
```

### Why Use Git Switch?

- **Clarity**: Single purpose - switching branches
- **Safety**: Less likely to accidentally overwrite files
- **Modern**: Part of Git's effort to simplify the interface
- **Explicit**: More obvious what the command does

## Branch Naming Conventions

Consistent naming conventions make it easier to understand the purpose of branches and maintain a clean repository.

### Common Patterns

#### Feature Branches
```
feature/user-authentication
feature/payment-integration
feature/dashboard-redesign
feat/add-dark-mode
```

#### Bug Fix Branches
```
bugfix/login-error
bugfix/memory-leak
fix/navbar-alignment
hotfix/critical-security-patch
```

#### Release Branches
```
release/v1.2.0
release/2024-01-sprint
```

#### Experimental Branches
```
experiment/new-architecture
experimental/ai-integration
spike/performance-testing
```

#### Documentation Branches
```
docs/api-documentation
docs/update-readme
```

### Naming Best Practices

1. **Use Lowercase**: `feature/login` not `Feature/Login`
2. **Use Hyphens**: `feature/user-auth` not `feature/user_auth` or `feature/userauth`
3. **Be Descriptive**: `feature/add-oauth-support` not `feature/oauth`
4. **Include Issue Numbers**: `feature/123-user-profile` or `bugfix/456-fix-crash`
5. **Keep It Short**: Aim for clarity without being verbose
6. **Avoid Special Characters**: Stick to alphanumeric characters and hyphens
7. **Use Prefixes**: Group related branches with prefixes

### Example Convention

```
<type>/<issue-number>-<short-description>

Examples:
feature/234-add-user-authentication
bugfix/567-fix-login-redirect
hotfix/890-security-patch
docs/123-update-api-guide
```

### Team-Specific Conventions

```
# With developer initials
jd/feature/user-dashboard
sm/bugfix/payment-error

# With ticket system
JIRA-1234-add-reporting
PROJ-567-fix-memory-leak

# With date-based releases
release/2024.01.15
hotfix/2024.01.20
```

## Branch Strategies

Branch strategies define how teams organize their work across branches. The right strategy depends on your team size, release cadence, and workflow.

### Git Flow

A comprehensive branching model with multiple long-lived branches.

```
main (production-ready code)
├── develop (integration branch)
│   ├── feature/feature-a
│   ├── feature/feature-b
│   └── feature/feature-c
├── release/v1.2.0
└── hotfix/critical-bug
```

**Branches:**
- `main`: Production-ready code
- `develop`: Integration branch for features
- `feature/*`: New features (branch from develop)
- `release/*`: Release preparation (branch from develop)
- `hotfix/*`: Production fixes (branch from main)

**Workflow:**
1. Create feature branches from `develop`
2. Merge features back to `develop`
3. Create release branch from `develop`
4. Merge release to both `main` and `develop`
5. Tag releases on `main`
6. Create hotfix branches from `main`
7. Merge hotfixes to both `main` and `develop`

**Best For:** Complex projects with scheduled releases and multiple versions in production.

### GitHub Flow

A simpler, more streamlined workflow focused on continuous deployment.

```
main (always deployable)
├── feature/user-login
├── feature/payment-system
└── bugfix/navbar-issue
```

**Branches:**
- `main`: Always deployable, production code
- `feature/*` or descriptive names: All work happens here

**Workflow:**
1. Create a branch from `main`
2. Make changes and commit
3. Open a pull request
4. Review and discuss
5. Deploy for testing (optional)
6. Merge to `main`
7. Deploy to production

**Best For:** Teams practicing continuous deployment, web applications, small to medium teams.

### GitLab Flow

Bridges Git Flow and GitHub Flow, adding environment branches.

```
main
├── feature/new-dashboard
├── production (deployed to production)
└── staging (deployed to staging)
```

**Branches:**
- `main`: Current development
- Environment branches: `production`, `staging`, `pre-production`
- Feature branches: Short-lived topic branches

**Workflow:**
1. Create feature branches from `main`
2. Merge to `main` via merge request
3. Cherry-pick or merge to environment branches
4. Deploy environment branches automatically

**Best For:** Projects with multiple environments and deployment stages.

### Trunk-Based Development

Developers work on short-lived branches or directly on the main branch.

```
main (trunk)
├── short-lived-feature (< 2 days)
└── another-feature (< 2 days)
```

**Key Principles:**
- Keep branches short-lived (hours to 2 days max)
- Commit to `main` frequently
- Use feature flags for incomplete features
- Rely on automated testing
- Deploy frequently

**Workflow:**
1. Create short-lived branch or work on `main`
2. Make small, incremental changes
3. Merge quickly (multiple times per day)
4. Use feature toggles for WIP features
5. Deploy continuously

**Best For:** High-performing teams, mature CI/CD pipelines, continuous deployment.

### Release Flow

Microsoft's strategy combining aspects of Git Flow and GitHub Flow.

```
main (current release)
├── topic/feature-a
├── topic/feature-b
└── release/v1.2.0 (stabilization)
```

**Branches:**
- `main`: Represents the current release
- `topic/*`: Features and fixes
- `release/*`: Release stabilization and bug fixes

**Workflow:**
1. Branch from `main` for features
2. Merge features to `main` continuously
3. Create release branch when ready
4. Bug fixes go to release branch
5. Cherry-pick critical fixes to `main`
6. Merge release branch back to `main` when shipped

**Best For:** Products with scheduled releases and stabilization periods.

### Choosing the Right Strategy

**Consider Git Flow if:**
- You have scheduled releases
- Multiple versions in production
- Large team with complex coordination needs

**Consider GitHub Flow if:**
- You practice continuous deployment
- Simple, fast-moving projects
- Small to medium teams

**Consider Trunk-Based Development if:**
- Mature CI/CD pipeline
- Experienced team
- Need high deployment frequency

**Consider GitLab Flow if:**
- Multiple deployment environments
- Staged rollout process
- Need environment-specific configurations

**Consider Release Flow if:**
- Scheduled releases with stabilization period
- Need to support multiple versions
- Balance between complexity and simplicity

## Best Practices

### General Branch Management

1. **Keep Branches Focused**: One branch = one feature/fix
2. **Delete Merged Branches**: Clean up after merging
3. **Regular Updates**: Keep feature branches updated with main
4. **Commit Often**: Small, logical commits are easier to manage
5. **Write Descriptive Names**: Make the purpose clear
6. **Protect Important Branches**: Use branch protection rules
7. **Review Before Merging**: Use pull requests for code review

### Commands Summary

```bash
# Modern workflow (Git 2.23+)
git switch -c feature/new-feature  # Create and switch
git switch main                     # Switch back

# Traditional workflow
git checkout -b feature/new-feature # Create and switch
git checkout main                   # Switch back

# Branch management
git branch                          # List branches
git branch -d feature-name          # Delete merged branch
git branch -m new-name              # Rename branch

# Updating branches
git switch main
git pull
git switch feature-branch
git merge main                      # Or use rebase
```

This guide covers the fundamentals of Git branching, providing you with the knowledge to work effectively with branches in any workflow.
