# 📂 05 - GitHub Basics

This section covers everything required to connect **local Git with GitHub** and work professionally.

---

# 📄 1️⃣ creating-github-account.md

## 🔹 What is GitHub?

GitHub is:

* A cloud-based Git repository hosting platform
* Used for collaboration, CI/CD, version control
* Built on top of Git

---

## 🔹 Steps to Create GitHub Account

1. Go to: [https://github.com](https://github.com)
2. Click **Sign Up**
3. Enter:

   * Email
   * Password
   * Username
4. Verify email
5. Choose plan (Free is enough)

---

## 🔹 Important Settings After Signup

Go to:
⚙️ Settings →

### 1️⃣ Profile Settings

* Add profile photo
* Add bio
* Add location
* Add LinkedIn / portfolio

### 2️⃣ Email Settings

* Verify primary email
* Set commit email visibility

### 3️⃣ Security Settings

* Enable 2FA (Very Important)

---

## 🔹 GitHub Terminology

| Term         | Meaning                     |
| ------------ | --------------------------- |
| Repository   | Project folder              |
| Fork         | Copy of someone else’s repo |
| Clone        | Download repo locally       |
| Pull Request | Request to merge changes    |
| Issues       | Track bugs/features         |
| Actions      | CI/CD automation            |

---

# 📄 2️⃣ ssh-keys-setup.md

## 🔹 Why SSH?

Instead of entering username/password every time,
SSH allows secure authentication.

---

## 🔹 Step 1: Check Existing SSH Keys

```bash
ls -al ~/.ssh
```

Look for:

```
id_rsa
id_rsa.pub
```

---

## 🔹 Step 2: Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Press Enter for defaults.

---

## 🔹 Step 3: Start SSH Agent

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

## 🔹 Step 4: Copy Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy output.

---

## 🔹 Step 5: Add Key to GitHub

GitHub → Settings → SSH and GPG Keys → New SSH Key → Paste → Save

---

## 🔹 Step 6: Test Connection

```bash
ssh -T git@github.com
```

Expected:

```
Hi username! You've successfully authenticated.
```

---

## 🔹 SSH vs HTTPS

| Feature           | SSH         | HTTPS  |
| ----------------- | ----------- | ------ |
| Password Required | No          | Yes    |
| Setup Complexity  | Medium      | Easy   |
| Secure            | Very Secure | Secure |

---

# 📄 3️⃣ personal-access-tokens.md

## 🔹 Why Personal Access Tokens (PAT)?

GitHub removed password authentication for HTTPS.
Now you must use:

* SSH OR
* Personal Access Token (PAT)

---

## 🔹 What is PAT?

A secure token used instead of password.

---

## 🔹 Generate PAT

GitHub → Settings → Developer Settings → Personal Access Tokens → Fine-grained Tokens → Generate

Choose:

* Repository access
* Expiry date
* Permissions (Read/Write)

---

## 🔹 Use PAT with Git

When pushing:

```
Username: your_github_username
Password: paste_PAT_here
```

---

## 🔹 Store PAT Locally

```bash
git config --global credential.helper store
```

Or use:

```bash
git config --global credential.helper cache
```

---

## 🔹 Security Best Practices

* Never share token
* Set expiration
* Give minimum permissions

---

# 📄 4️⃣ creating-repositories.md

## 🔹 Types of Repositories

1. Public
2. Private
3. Internal (Enterprise)

---

## 🔹 Create Repository on GitHub

1. Click "+"
2. New Repository
3. Enter:

   * Repo name
   * Description
   * Public/Private
4. Add README (optional)
5. Click Create

---

## 🔹 Connect Local Project to GitHub

### If Repo is Empty:

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin git@github.com:username/repo.git
git branch -M main
git push -u origin main
```

---

## 🔹 If Repo Already Exists Locally

```bash
git remote add origin <repo-url>
git push -u origin main
```

---

## 🔹 Clone Repository

```bash
git clone git@github.com:username/repo.git
```

---

## 🔹 Check Remote

```bash
git remote -v
```

---

# 📄 5️⃣ readme-files.md

## 🔹 What is README?

README.md:

* Explains project
* First thing recruiter sees
* Written in Markdown

---

## 🔹 Markdown Basics

### Headings

```md
# Title
## Subtitle
```

### Bold & Italic

```md
**Bold**
*Italic*
```

### Code Block

````md
```bash
git clone repo-url
```
````

### Links

```md
[Google](https://google.com)
```

### Images

```md
![Alt Text](image-url)
```

---

## 🔹 Professional README Structure

```md
# Project Name

## Description
Brief explanation

## Features
- Feature 1
- Feature 2

## Tech Stack
- AWS
- Docker
- Python

## Installation
Steps

## Usage
How to run

## Screenshots

## Author
Harshada Patil
```

---

## 🔹 DevOps-Level README Must Include

* Architecture diagram
* Setup instructions
* Environment variables
* Deployment steps

---

# 📄 6️⃣ github-profile.md

## 🔹 Special Feature

If you create a repo with same name as username:

Example:
Username: `harshada`
Repo name: `harshada`

GitHub treats it as profile README.

---

## 🔹 Steps to Create Profile README

1. Create new repository
2. Name = your username
3. Add README
4. Save

---

## 🔹 What to Include in Profile

```md
# Hi 👋 I'm Harshada

🎓 B.Tech CSE Graduate  
☁️ Cloud & DevOps Enthusiast  
🐳 Docker | Kubernetes | AWS  

## 🚀 Skills
- AWS
- Terraform
- Docker
- Jenkins
- Linux

## 📌 Projects
- Love Travel (Full Stack)
- Docker Network Setup

## 📫 Contact
LinkedIn | Email
```

---

## 🔹 Add Badges

Use:
[https://shields.io/](https://shields.io/)

Example:

```md
![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
```

---

## 🔹 Add GitHub Stats

Use:
[https://github-readme-stats.vercel.app/](https://github-readme-stats.vercel.app/)

Example:

```md
![Stats](https://github-readme-stats.vercel.app/api?username=yourusername&show_icons=true)
```

---

# 🧠 Interview-Level Questions

1. Difference between SSH and HTTPS?
2. What is Personal Access Token?
3. How to connect local repo to GitHub?
4. What happens if remote origin already exists?
5. How to change remote URL?
6. How to fork and clone?

---

# 🔥 Real-World DevOps Scenario

Production repo → Use:

* Protected branches
* Required pull request reviews
* CI/CD via GitHub Actions
* Secrets for credentials

---

# ✅ Final Summary

| Topic          | Purpose                 |
| -------------- | ----------------------- |
| SSH            | Secure authentication   |
| PAT            | HTTPS authentication    |
| Remote         | Connect local to GitHub |
| README         | Project documentation   |
| Profile README | Personal branding       |


