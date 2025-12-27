# Git Diff - Viewing Changes

## Introduction

The `git diff` command shows differences between various states in your Git repository. It's essential for reviewing changes before committing and understanding what has been modified.

## Basic Usage

### Unstaged Changes
```bash
git diff
```
Shows changes in your working directory that haven't been staged yet (changes not added with `git add`).

### Staged Changes
```bash
git diff --staged
# or
git diff --cached
```
Shows changes that have been staged and are ready to be committed.

### All Changes
```bash
git diff HEAD
```
Shows all changes (both staged and unstaged) compared to the last commit.

## Understanding Diff Output

### Reading the Output

```diff
diff --git a/file.txt b/file.txt
index 83db48f..bf269f4 100644
--- a/file.txt
+++ b/file.txt
@@ -1,4 +1,4 @@
 This is line 1
-This is the old line 2
+This is the new line 2
 This is line 3
 This is line 4
```

**Components:**
- `---` indicates the original file
- `+++` indicates the modified file
- `@@` shows the line numbers affected
- `-` indicates removed lines (shown in red)
- `+` indicates added lines (shown in green)
- Unchanged lines are shown without prefix

## Comparing Commits

### Compare Two Commits
```bash
git diff commit1 commit2
```

### Compare with Specific Commit
```bash
git diff abc123
```
Shows changes between commit `abc123` and current working directory.

### Compare Last Two Commits
```bash
git diff HEAD~1 HEAD
```

### Compare with Parent Commit
```bash
git diff HEAD^
```

## Comparing Branches

### Compare Current Branch with Another
```bash
git diff main
```

### Compare Two Branches
```bash
git diff branch1..branch2
```

### Three-Dot Comparison
```bash
git diff branch1...branch2
```
Shows changes in `branch2` since it diverged from `branch1`.

## File-Specific Diffs

### Single File
```bash
git diff filename.txt
```

### Multiple Files
```bash
git diff file1.txt file2.txt
```

### Specific Directory
```bash
git diff src/
```

## Output Options

### Summary Only
```bash
git diff --stat
```
Shows which files changed and how many lines were added/removed.

### Name Only
```bash
git diff --name-only
```
Lists only the names of changed files.

### Name and Status
```bash
git diff --name-status
```
Shows file names with modification status (A=Added, M=Modified, D=Deleted).

### Ignore Whitespace
```bash
git diff -w
# or
git diff --ignore-all-space
```

### Ignore Whitespace at Line Ends
```bash
git diff --ignore-space-at-eol
```

## Word-Level Diffs

### Word Diff
```bash
git diff --word-diff
```
Shows changes at the word level rather than line level.

### Color Words
```bash
git diff --color-words
```
Highlights changed words with color.

## Advanced Filtering

### Show Only File Names
```bash
git diff --name-only HEAD~5
```

### Filter by File Type
```bash
git diff -- '*.js'
```

### Exclude Files
```bash
git diff -- . ':!*.log'
```
Shows all changes except log files.

## Comparing Stashes

### Compare with Stash
```bash
git diff stash@{0}
```

### Compare Stash Entries
```bash
git diff stash@{0} stash@{1}
```

## Practical Examples

### Before Staging
```bash
# See what you're about to stage
git diff

# Stage the changes
git add .

# See what you're about to commit
git diff --staged
```

### Compare Today's Work
```bash
git diff @{yesterday} HEAD
```

### Changes in Last Commit
```bash
git diff HEAD~1 HEAD
```

### Changes in Specific Commit
```bash
git show abc123
# or
git diff abc123^!
```

### Compare File Across Branches
```bash
git diff main..feature -- src/app.js
```

## Output Formatting

### Unified Diff Context
```bash
# Show 10 lines of context instead of default 3
git diff -U10
```

### Minimal Output
```bash
git diff --minimal
```

### Patience Algorithm
```bash
git diff --patience
```
Uses a different algorithm that sometimes produces more readable diffs.

### Histogram Algorithm
```bash
git diff --histogram
```

## External Diff Tools

### Configure External Tool
```bash
git config --global diff.tool vimdiff
```

### Use External Tool
```bash
git difftool
```

### Available Tools
Common diff tools include:
- vimdiff
- meld
- kdiff3
- opendiff (Mac)
- Beyond Compare

## Binary Files

### Show Binary File Names
```bash
git diff --binary
```

### Summary of Binary Changes
```bash
git diff --stat
```

## Creating Patches

### Create Patch File
```bash
git diff > changes.patch
```

### Apply Patch
```bash
git apply changes.patch
```

## Diff with Tags

### Compare with Tag
```bash
git diff v1.0 v2.0
```

### Changes Since Tag
```bash
git diff v1.0..HEAD
```

## Tips and Tricks

### 1. Colorization
```bash
git config --global color.diff auto
```

### 2. Better Diffs for Moved Code
```bash
git diff --color-moved
```

### 3. Show Function Names
```bash
git diff -p
```

### 4. Ignore File Mode Changes
```bash
git diff --no-ext-diff
```

### 5. Reverse Diff
```bash
git diff -R
```

## Common Workflows

### Pre-Commit Review
```bash
# Review unstaged changes
git diff

# Stage changes
git add file.txt

# Review staged changes
git diff --staged

# Commit
git commit -m "message"
```

### Comparing Feature Branch
```bash
# See what your feature branch changed
git diff main...feature-branch

# See specific file changes
git diff main...feature-branch -- src/app.js
```

### Review Pull Request Changes
```bash
git fetch origin pull/123/head:pr-123
git diff main..pr-123
```

## Aliases

Create useful aliases:

```bash
git config --global alias.d "diff"
git config --global alias.ds "diff --staged"
git config --global alias.dw "diff --word-diff"
git config --global alias.dt "difftool"
```

## Integration with Other Commands

### Diff with Log
```bash
git log -p
```
Shows commit history with diffs.

### Diff with Show
```bash
git show abc123
```
Shows commit details and its diff.

### Diff with Grep
```bash
git diff | grep "specific pattern"
```

## Performance Considerations

For large repositories:

```bash
# Show only names and status for speed
git diff --name-status

# Limit diff output
git diff --stat

# Skip binary files
git diff --text
```

