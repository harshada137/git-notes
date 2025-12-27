# Git Log - Viewing Commit History

## Introduction

The `git log` command displays the commit history of your repository. It's one of the most frequently used commands for understanding what changes have been made and by whom.

## Basic Usage

### Simple Log
```bash
git log
```
Shows the commit history with full details including commit hash, author, date, and message.

### One-Line Format
```bash
git log --oneline
```
Displays each commit on a single line with abbreviated hash and commit message.

### Limited Number of Commits
```bash
git log -n 5
# or
git log -5
```
Shows only the last 5 commits.

## Formatting Options

### Pretty Formats
```bash
# Short format
git log --pretty=short

# Full format
git log --pretty=full

# Custom format
git log --pretty=format:"%h - %an, %ar : %s"
```

**Format placeholders:**
- `%h` - Abbreviated commit hash
- `%H` - Full commit hash
- `%an` - Author name
- `%ae` - Author email
- `%ad` - Author date
- `%ar` - Author date, relative
- `%cn` - Committer name
- `%s` - Commit subject (message)
- `%b` - Commit body

### Example Custom Format
```bash
git log --pretty=format:"%C(yellow)%h%C(reset) %C(blue)%ad%C(reset) %C(green)%an%C(reset) %s" --date=short
```
This creates a colorized log with hash, date, author, and message.

## Filtering Commits

### By Author
```bash
git log --author="John Doe"
```

### By Date
```bash
# Since a specific date
git log --since="2024-01-01"

# Until a specific date
git log --until="2024-12-31"

# Last 2 weeks
git log --since="2 weeks ago"
```

### By Commit Message
```bash
git log --grep="bug fix"
```

### By File
```bash
git log -- filename.txt
```
Shows commits that modified a specific file.

### By Content
```bash
git log -S "function_name"
```
Shows commits that added or removed the specified string.

## Visual Representations

### Graph View
```bash
git log --graph --oneline --all
```
Shows a text-based graph of the branch structure.

### Decorated Log
```bash
git log --oneline --decorate
```
Shows branch and tag names alongside commits.

### All Branches
```bash
git log --all
```
Shows commits from all branches.

## Detailed Information

### Show Changes (Patch)
```bash
git log -p
```
Shows the actual changes (diff) introduced in each commit.

### Statistics
```bash
git log --stat
```
Shows which files were changed and the number of lines added/removed.

### Short Statistics
```bash
git log --shortstat
```
Shows only the changed/insertions/deletions line.

## Practical Examples

### Last 10 Commits with Graph
```bash
git log --graph --oneline --decorate -10
```

### Commits by Specific Author in Last Month
```bash
git log --author="Jane" --since="1 month ago"
```

### Files Changed in Recent Commits
```bash
git log --name-only -5
```

### Commits Affecting Specific Directory
```bash
git log -- src/components/
```

### Merge Commits Only
```bash
git log --merges
```

### Non-Merge Commits Only
```bash
git log --no-merges
```

## Advanced Usage

### Compare Branches
```bash
# Commits in branch1 but not in branch2
git log branch1..branch2

# Commits in branch2 but not in branch1
git log branch2..branch1
```

### Show Commits Between Tags
```bash
git log v1.0..v2.0
```

### Follow File Renames
```bash
git log --follow filename.txt
```

### Reverse Order (Oldest First)
```bash
git log --reverse
```

## Combining Options

You can combine multiple options for powerful queries:

```bash
git log --graph --oneline --all --decorate --author="John" --since="1 week ago"
```

## Creating Aliases

Save frequently used log commands as aliases:

```bash
git config --global alias.lg "log --graph --oneline --decorate --all"
git config --global alias.last "log -1 HEAD --stat"
```

Now you can use:
```bash
git lg
git last
```

## Tips

1. Use `q` to quit the log view
2. Use `/` to search within the log
3. Use `Space` to scroll down, `b` to scroll up
4. Pipe to `less` for better navigation: `git log | less`
5. Use `--oneline` for quick overviews
6. Use `--graph` to visualize branch structure

## Common Patterns

```bash
# Quick overview of recent work
git log --oneline -10

# Detailed look at last commit
git log -1 -p

# What changed today
git log --since="midnight" --author="$(git config user.name)"

# Beautiful branch visualization
git log --graph --pretty=format:'%C(yellow)%h%C(reset) -%C(red)%d%C(reset) %s %C(green)(%cr) %C(blue)<%an>%C(reset)' --abbrev-commit --date=relative
```

