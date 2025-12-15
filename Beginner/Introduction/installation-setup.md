# Installation & Setup (Git)
This section covers **installing Git** on different operating systems and performing the **initial configuration** required before using Git in real projects.


## 1. Installing Git on Windows
### Step 1: Download Git

* Visit the official Git website: [https://git-scm.com](https://git-scm.com)
* Download the **64-bit Git for Windows** installer

### Step 2: Run the Installer

During installation, keep the following options selected (recommended):

* **Select Components**:

  * Git Bash Here ✔
  * Git GUI Here ✔
  * Associate .git* configuration files ✔

* **Default Editor**: Choose one

  * Vim (default) or
  * VS Code (recommended if installed)

* **Adjusting PATH environment**:

  * Select: **Git from the command line and also from 3rd-party software**

* **HTTPS transport backend**:

  * Use the OpenSSL library

* **Line Ending Conversions**:

  * Checkout Windows-style, commit Unix-style line endings

* **Terminal Emulator**:

  * Use MinTTY (default terminal for Git Bash)

* **Extra Options**:

  * Enable file system caching ✔
  * Enable symbolic links ✔ (optional)

Click **Install** and wait for completion.

### Step 3: Verify Installation

Open **Git Bash** or **Command Prompt** and run:

```bash
git --version
```

If Git is installed correctly, the version number will be displayed.

---

## 2. Installing Git on Linux

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install git -y
```

### CentOS / RHEL / Rocky Linux

```bash
sudo yum install git -y
```

### Fedora

```bash
sudo dnf install git -y
```

### Verify Installation

```bash
git --version
```

---

## 3. Installing Git on macOS

### Using Homebrew (Recommended)

```bash
brew install git
```

### Using Xcode Command Line Tools

```bash
xcode-select --install
```

Verify:

```bash
git --version
```

---

## 4. Initial Git Configuration (Required)

After installation, Git must be configured with user information.

### Set Username

```bash
git config --global user.name "Your Name"
```

### Set Email Address

```bash
git config --global user.email "youremail@example.com"
```

These details are attached to every commit you make.

---

## 5. Configure Default Branch Name

To set the default branch name as `main`:

```bash
git config --global init.defaultBranch main
```

---

## 6. Configure Default Editor

### Set VS Code as Default Editor

```bash
git config --global core.editor "code --wait"
```

### Set Vim as Default Editor

```bash
git config --global core.editor vim
```

---

## 7. Check Git Configuration

To view all global settings:

```bash
git config --global --list
```

To view a specific value:

```bash
git config user.name
git config user.email
```

---

## 8. Create and Initialize a Git Repository

### Create Project Folder

```bash
mkdir my-project
cd my-project
```

### Initialize Git Repository

```bash
git init
```

This creates a hidden `.git` directory which stores all version history.

---

## 9. Basic Folder Status Check

```bash
git status
```

Shows:

* Untracked files
* Modified files
* Staged files

---

## 10. Common Setup Troubleshooting

### Git Command Not Found (Windows)

* Restart terminal
* Reinstall Git and ensure PATH option is selected

### Permission Issues (Linux)

```bash
sudo chown -R $USER:$USER .git
```

---

## Summary

After completing installation and setup:

* Git is installed and verified
* User identity is configured
* Default branch and editor are set
* Repository is ready for version control

