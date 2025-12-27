# Viewing History - Understanding Your Repository's Past

## Introduction

Git provides powerful tools to explore your repository's history. Understanding how to view and analyze past changes is essential for debugging, understanding code evolution, and collaborating with others.

## Basic History Commands

### git log
The primary command for viewing commit history.

```bash
# Standard log
git log

# Compact one-line view
git log --oneline

# Last 5 commits
git log -5
```

### git show
View detailed information about a specific commit.

```bash
# Show last commit
git show

# Show specific commit
git show abc123

# Show specific file from commit
git show abc123:path/to/file.txt
```

### git reflog
Shows a log of all reference updates (even undone operations).

```bash
# View reflog
git reflog

# Show last 10 entries
git reflog -10
```

## Viewing Commit Details

### Full Commit Information
```bash
# Complete details of last commit
git show HEAD

# Details of specific commit
git show <commit-hash>
```

### Commit Content
```bash
# Show commit with full diff
git show abc123

# Show only the commit message
git log --format=%B -n 1 abc123

# Show files changed in commit
git show --name-only abc123
```

### Commit Statistics
```bash
# Show stats for commit
git show --stat abc123

# Short statistics
git show --shortstat abc123
```

## Filtering History

### By Author
```bash
# Commits by specific author
git log --author="John Doe"

# Multiple authors
git log --author="John\|Jane"
```

### By Date Range
```bash
# Since specific date
git log --since="2024-01-01"

# Before specific date
git log --until="2024-12-31"

# Between dates
git log --since="2024-01-01" --until="2024-12-31"

# Relative dates
git log --since="2 weeks ago"
git log --since="3 months ago"
git log --after="yesterday"
```

### By Commit Message
```bash
# Search commit messages
git log --grep="bug fix"

# Case-insensitive search
git log --grep="feature" -i

# Multiple patterns
git log --grep="bug\|fix"
```

### By File or Directory
```bash
# Commits affecting specific file
git log -- filename.txt

# Commits in specific directory
git log -- src/components/

# Multiple files
git log -- file1.txt file2.txt

# Follow file through renames
git log --follow -- filename.txt
```

### By Content Changes
```bash
# Find commits that added/removed string
git log -S "function_name"

# With regex
git log -G "regex_pattern"

# Show the actual changes
git log -S "function_name" -p
```

## Visualizing History

### Branch Graph
```bash
# Text-based graph
git log --graph --oneline --all

# Decorated graph (shows branches and tags)
git log --graph --oneline --decorate --all

# Pretty graph with colors
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

### Visual Tools
```bash
# Git's built-in GUI
gitk

# Alternative graphical view
git log --all --graph --decorate --oneline --simplify-by-decoration
```

## Comparing History

### Between Commits
```bash
# Changes between two commits
git log commit1..commit2

# Show actual diffs
git log -p commit1..commit2

# Just the files changed
git log --name-only commit1..commit2
```

### Between Branches
```bash
# Commits in feature not in main
git log main..feature

# Commits in main not in feature
git log feature..main

# Symmetric difference (commits unique to each)
git log --left-right main...feature
```

### Between Tags
```bash
# Changes between versions
git log v1.0..v2.0

# With statistics
git log --stat v1.0..v2.0
```

## Viewing File History

### Complete File History
```bash
# All commits that touched file
git log -- filename.txt

# With diffs
git log -p -- filename.txt

# Following renames
git log --follow -- filename.txt
```

### File at Specific Point
```bash
# View file from specific commit
git show commit-hash:path/to/file.txt

# View file from branch
git show branch-name:path/to/file.txt

# View file from tag
git show v1.0:path/to/file.txt
```

### Who Changed What (git blame)
```bash
# Line-by-line authorship
git blame filename.txt

# With line numbers
git blame -L 10,20 filename.txt

# Show email addresses
git blame -e filename.txt

# Ignore whitespace changes
git blame -w filename.txt

# Show original commit
git blame -C filename.txt
```

## Searching History

### Find When Bug Was Introduced
```bash
# Binary search for bug
git bisect start
git bisect bad              # Current version is bad
git bisect good v1.0        # v1.0 was good
# Git will checkout commits for you to test
git bisect good/bad         # Mark each test
git bisect reset            # When done
```

### Search All Commits
```bash
# Search for string in all commits
git log -S "search_string" --source --all

# Search with regex
git log -G "regex_pattern" --all

# Find when file was deleted
git log --all --full-history -- path/to/file.txt
```

## Advanced History Queries

### Merge Commits
```bash
# Show only merges
git log --merges

# Exclude merges
git log --no-merges

# Show merge commit parents
git log --first-parent
```

### Commit Ancestry
```bash
# Parent of commit
git show HEAD^
git show HEAD~1

# Grandparent
git show HEAD^^
git show HEAD~2

# First parent of merge commit
git show HEAD^1

# Second parent of merge commit
git show HEAD^2
```

### Multiple Branch History
```bash
# History of multiple branches
git log branch1 branch2 branch3

# Commits in any branch
git log --all

# Exclude specific branches
git log --all --not --remotes=origin/main
```

## Formatting Output

### Custom Formats
```bash
# Basic custom format
git log --pretty=format:"%h - %an, %ar : %s"

# Detailed custom format
git log --pretty=format:"%C(yellow)%h%Creset %C(blue)%ad%Creset %C(red)|%Creset %C(green)%s%Creset %C(bold blue)[%an]%Creset" --date=short

# JSON-like format
git log --pretty=format:'{"commit": "%H","author": "%an","date": "%ad","message": "%s"},'
```

### Format Placeholders
Common placeholders:
- `%H` - Full commit hash
- `%h` - Abbreviated hash
- `%an` - Author name
- `%ae` - Author email
- `%ad` - Author date
- `%ar` - Author date, relative
- `%cn` - Committer name
- `%s` - Subject (message)
- `%b` - Body

### Date Formats
```bash
# Different date formats
git log --date=relative
git log --date=short
git log --date=local
git log --date=iso
git log --date=rfc
git log --date=format:'%Y-%m-%d %H:%M'
```

## Performance Tips

### For Large Repositories
```bash
# Limit output
git log -n 100

# Simplified commits
git log --oneline --no-merges

# Skip diff calculation
git log --no-patch

# Shallow history
git log --since="1 month ago"
```

### Faster Searches
```bash
# Search in commit messages only
git log --grep="pattern" --oneline

# Use pathspec for specific files
git log -- '*.js'

# Limit to specific branch
git log main --since="1 week ago"
```

## Practical Workflows

### Daily Development Review
```bash
# What did I do today?
git log --author="$(git config user.name)" --since="midnight" --oneline

# What changed since yesterday?
git log --since="yesterday" --oneline

# Recent commits with details
git log -10 --stat
```

### Code Review
```bash
# Review feature branch
git log main..feature --oneline

# Detailed review with diffs
git log main..feature -p

# Files changed in feature
git log main..feature --name-status
```

### Bug Investigation
```bash
# When was function added?
git log -S "functionName" --source --all

# Who last modified this line?
git blame -L 100,100 file.txt

# Find commit that broke feature
git bisect start
git bisect bad HEAD
git bisect good v1.0
```

### Release Preparation
```bash
# Changes since last release
git log v1.0..HEAD --oneline

# Summary of changes
git log v1.0..HEAD --oneline --no-merges | wc -l

# Detailed changelog
git log v1.0..HEAD --pretty=format:"- %s (%an)" --no-merges
```

## Useful Aliases

Create shortcuts for common history commands:

```bash
# Basic aliases
git config --global alias.lg "log --graph --oneline --decorate --all"
git config --global alias.last "log -1 HEAD --stat"
git config --global alias.today "log --since=midnight --author='$(git config user.name)' --oneline"

# Advanced aliases
git config --global alias.ll "log --graph --pretty=format:'%C(yellow)%h%C(red)%d%C(reset) - %C(bold green)(%ar)%C(reset) %s %C(blue)<%an>%C(reset)' --abbrev-commit --date=relative"

git config --global alias.filelog "log -u"
git config --global alias.who "shortlog -sn --"
```

## Common Patterns

### Find Lost Work
```bash
# View all reference changes
git reflog

# Recover lost commit
git checkout <commit-hash>

# See what was in old commit
git show <commit-hash>
```

### Understand Branch Divergence
```bash
# Visualize branch relationship
git log --graph --oneline main feature

# Commits unique to each branch
git log --left-right --oneline main...feature

# Find merge base
git merge-base main feature
```

### Track File Movement
```bash
# Find when file was renamed
git log --follow --all -- current-filename.txt

# Find deleted file
git log --all --full-history -- deleted-file.txt

# Restore deleted file
git checkout <commit-hash>^ -- deleted-file.txt
```

## Integration with Other Tools

### Exporting History
```bash
# Generate changelog
git log v1.0..v2.0 --pretty=format:"* %s" --no-merges > CHANGELOG.md

# Create release notes
git log --since="1 month ago" --pretty=format:"- %s (%an)" > release-notes.txt

# Export to CSV
git log --pretty=format:'"%h","%an","%ad","%s"' --date=short > commits.csv
```

### Piping to Other Commands
```bash
# Count commits by author
git log --format='%an' | sort | uniq -c | sort -nr

# Find most changed files
git log --pretty=format: --name-only | sort | uniq -c | sort -nr | head -10

# Commits per day
git log --format='%ad' --date=short | sort | uniq -c
```

