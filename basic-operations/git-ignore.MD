# .gitignore - Excluding Files from Git

## Introduction

The `.gitignore` file tells Git which files or directories to ignore in a project. This prevents unnecessary or sensitive files from being tracked and committed to your repository.

## Creating a .gitignore File

### Basic Creation
```bash
# In your project root
touch .gitignore
```

Then edit the file with your preferred text editor.

### Common Location
The `.gitignore` file is typically placed in the root directory of your repository, but you can also have `.gitignore` files in subdirectories.

## Basic Syntax

### Ignore Specific Files
```gitignore
# Ignore a specific file
secrets.txt
config.local.js
```

### Ignore by Extension
```gitignore
# Ignore all .log files
*.log

# Ignore all .tmp files
*.tmp
```

### Ignore Directories
```gitignore
# Ignore a directory and its contents
node_modules/
dist/
build/

# Note: Include trailing slash for directories
```

### Comments
```gitignore
# This is a comment
# Comments start with #
```

## Pattern Matching

### Wildcards
```gitignore
# Asterisk (*) matches any string
*.txt         # All .txt files
temp*         # Files starting with "temp"
*_backup      # Files ending with "_backup"
```

### Question Mark
```gitignore
# Question mark (?) matches single character
file?.txt     # Matches file1.txt, fileA.txt, etc.
```

### Double Asterisk
```gitignore
# Match in all directories
**/logs       # logs folder anywhere
**/debug.log  # debug.log anywhere

# Match any subdirectories
docs/**       # Everything under docs/
```

### Ranges
```gitignore
# Bracket expressions
file[0-9].txt     # Matches file0.txt through file9.txt
test[abc].js      # Matches testa.js, testb.js, testc.js
```

## Negation (Exceptions)

### Un-ignore Files
```gitignore
# Ignore all .log files
*.log

# But track important.log
!important.log
```

### Un-ignore in Subdirectory
```gitignore
# Ignore everything in logs/
logs/*

# But keep a specific file
!logs/important.log

# And keep a subdirectory
!logs/keep/
```

## Common Patterns

### Node.js
```gitignore
# Dependencies
node_modules/
npm-debug.log
yarn-error.log
package-lock.json
yarn.lock

# Build outputs
dist/
build/
.next/
out/

# Environment variables
.env
.env.local
.env.*.local

# IDE
.vscode/
.idea/

# OS files
.DS_Store
Thumbs.db
```

### Python
```gitignore
# Byte-compiled
__pycache__/
*.py[cod]
*$py.class

# Virtual environments
venv/
env/
ENV/
.venv

# Distribution
dist/
build/
*.egg-info/

# Testing
.pytest_cache/
.coverage
htmlcov/

# Jupyter
.ipynb_checkpoints

# IDE
.vscode/
.idea/
*.swp
*.swo
```

### Java
```gitignore
# Compiled class files
*.class

# Package files
*.jar
*.war
*.ear

# Maven
target/
pom.xml.tag
pom.xml.releaseBackup

# Gradle
.gradle/
build/

# IDE
.idea/
*.iml
.classpath
.project
.settings/

# Log files
*.log
```

### React/Frontend
```gitignore
# Dependencies
node_modules/
.pnp/
.pnp.js

# Testing
coverage/

# Production
build/
dist/

# Misc
.DS_Store
.env.local
.env.development.local
.env.test.local
.env.production.local

# Logs
npm-debug.log*
yarn-debug.log*
yarn-error.log*
```

### C/C++
```gitignore
# Object files
*.o
*.obj
*.ko
*.elf

# Executables
*.exe
*.out
*.app
*.bin

# Libraries
*.a
*.lib
*.so
*.dylib

# Debug files
*.dSYM/
*.su
```

## Global .gitignore

### Setting Up Global Ignore
```bash
# Create global gitignore file
touch ~/.gitignore_global

# Configure Git to use it
git config --global core.excludesfile ~/.gitignore_global
```

### Common Global Patterns
```gitignore
# OS generated files
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
Thumbs.db
Desktop.ini

# Editor files
*.swp
*.swo
*~
.vscode/
.idea/
*.sublime-project
*.sublime-workspace

# Temporary files
*.tmp
*.temp
*.bak
```

## Advanced Techniques

### Ignore Everything Except
```gitignore
# Ignore everything
*

# But not these files
!.gitignore
!README.md
!src/

# And not in src
!src/**
```

### Directory-Specific Ignores
```gitignore
# Ignore PDFs only in the root
/*.pdf

# Ignore PDFs everywhere
**/*.pdf

# Ignore PDFs only in docs/
docs/*.pdf
```

### Conditional Ignoring
```gitignore
# Ignore all txt files in root
/*.txt

# Except in specific directory
!/important/*.txt
```

## Checking Ignored Files

### See What's Being Ignored
```bash
git status --ignored
```

### Check If File Is Ignored
```bash
git check-ignore -v filename.txt
```
This shows which rule is causing the file to be ignored.

### List All Ignored Files
```bash
git ls-files --ignored --exclude-standard --others
```

## Untracking Already-Committed Files

### Remove from Repository but Keep Locally
```bash
# Single file
git rm --cached filename.txt

# Directory
git rm -r --cached directory/

# Then commit
git commit -m "Remove tracked file"
```

### Stop Tracking and Add to .gitignore
```bash
# Add to .gitignore
echo "secrets.txt" >> .gitignore

# Remove from Git
git rm --cached secrets.txt

# Commit
git commit -m "Untrack secrets.txt"
```

## Templates and Resources

### GitHub's Gitignore Templates
Visit: https://github.com/github/gitignore

Provides templates for:
- Programming languages
- Frameworks
- IDEs
- Operating systems

### Using Templates
```bash
# Download Node.js template
curl https://raw.githubusercontent.com/github/gitignore/main/Node.gitignore -o .gitignore
```

## Troubleshooting

### File Still Being Tracked
If a file is already tracked, adding it to `.gitignore` won't help:

```bash
# First, untrack it
git rm --cached filename

# Then ensure it's in .gitignore
echo "filename" >> .gitignore

# Commit
git commit -m "Untrack filename"
```

### Check Ignore Rules
```bash
# See which rule affects a file
git check-ignore -v path/to/file

# See all ignored files with their rules
git check-ignore -v *
```

### Clear Git Cache
If gitignore isn't working as expected:

```bash
# Remove all cached files
git rm -r --cached .

# Re-add everything
git add .

# Commit
git commit -m "Fix gitignore"
```

## Best Practices

### 1. Commit .gitignore Early
Add and commit your `.gitignore` file before adding other files to the repository.

### 2. Be Specific
```gitignore
# Good - specific
node_modules/
dist/build/

# Bad - too broad
*
```

### 3. Document Unusual Rules
```gitignore
# Keep API keys safe
.env

# Exclude large data files (> 100MB)
data/*.csv

# IDE-specific (for Visual Studio)
*.suo
```

### 4. Use Comments
```gitignore
# === Dependencies ===
node_modules/
vendor/

# === Build outputs ===
dist/
build/

# === Environment ===
.env
.env.local
```

### 5. Separate Concerns
Consider multiple `.gitignore` files:
- Root: General project ignores
- Subdirectories: Specific to that module

### 6. Never Commit Sensitive Data
```gitignore
# Credentials and keys
*.pem
*.key
.env
secrets.json
credentials.txt

# Database files
*.db
*.sqlite
*.sqlite3
```

## .gitignore vs .git/info/exclude

### Local Exclusions
If you want to ignore files only in your local copy:

```bash
# Edit .git/info/exclude
nano .git/info/exclude
```

This won't be shared with others but works the same as `.gitignore`.

### When to Use Each
- **`.gitignore`**: For patterns everyone on the project should ignore
- **`.git/info/exclude`**: For personal preferences not relevant to others

## Real-World Example

```gitignore
# === Operating System ===
.DS_Store
Thumbs.db
*.swp

# === IDE ===
.vscode/
.idea/
*.sublime-*

# === Dependencies ===
node_modules/
vendor/
packages/

# === Environment ===
.env
.env.local
.env.*.local
!.env.example

# === Build ===
dist/
build/
out/
*.min.js
*.min.css

# === Logs ===
logs/
*.log
npm-debug.log*

# === Testing ===
coverage/
.nyc_output/
.pytest_cache/

# === Temporary ===
tmp/
temp/
*.tmp
*.cache

# === Documentation ===
# Keep docs but ignore generated API docs
/docs/api/

# === Custom ===
# Project-specific ignores
data/raw/
experiments/
scratch/
```

