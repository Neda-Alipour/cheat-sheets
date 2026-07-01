
# 🟩 Git & GitHub Cheat Sheet (Complete Beginner → Intermediate)

---

# 🧠 Git vs GitHub

| Git                                                 | GitHub                              |
| --------------------------------------------------- | ----------------------------------- |
| Version control software installed on your computer | Website that hosts Git repositories |
| Works offline                                       | Requires internet                   |
| Tracks code history                                 | Stores repositories online          |
| `git` command                                       | github.com                          |

---

# ⚙️ First-Time Setup (One Time Only)

## 1. Install Git

```bash
git --version
```

Example:

```text
git version 2.xx.x
```

---

## 2. Configure Your Identity

```bash
git config --global user.name "your_name"

git config --global user.email "your_email@example.com"

git config --list
```

---

## 3. Generate SSH Key (Recommended)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

When asked:

```
Enter file in which to save the key:
```

➡ Press **Enter**

When asked:

```
Enter passphrase:
```

➡ Press **Enter** (or create one)

---

## 4. Enable SSH Agent (Windows)

Run **PowerShell as Administrator**

```powershell
Set-Service ssh-agent -StartupType Automatic
```

```powershell
Start-Service ssh-agent
```

Check:

```powershell
Get-Service ssh-agent
```

Should say:

```
Running
```

---

## 5. Add Your SSH Key

```powershell
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

---

## 6. Copy Your Public Key

```powershell
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub
```

or

```powershell
cat $env:USERPROFILE\.ssh\id_ed25519.pub
```

Copy everything.

---

## 7. Add the Key to GitHub

GitHub

↓

Settings

↓

SSH and GPG Keys

↓

New SSH Key

↓

Paste your key

---

## 8. Test SSH

```bash
ssh -T git@github.com
```

Expected:

```
Hi username!

You've successfully authenticated...
```

---

# 🔐 HTTPS Authentication (Alternative)

If your remote starts with

```
https://github.com/...
```

GitHub **does NOT use your password anymore.**

Use a **Personal Access Token (PAT)** instead.

GitHub

↓

Settings

↓

Developer Settings

↓

Personal Access Tokens

↓

Generate New Token

---

# 📁 Creating Repositories

Initialize repository

```bash
git init
```

Clone repository

```bash
git clone <url>
```

Clone into folder

```bash
git clone <url> my-folder
```

---

# 🌍 Remote Repositories

Show remotes

```bash
git remote -v
```

Add remote

```bash
git remote add origin <url>
```

Change remote

```bash
git remote set-url origin <url>
```

Remove remote

```bash
git remote remove origin
```

---

# 🔍 Check Current Branch

```bash
git branch
```

Current branch has *

---

# 📄 Status

```bash
git status
```

Shows

* modified files
* staged files
* untracked files

---

# ➕ Stage Changes

One file

```bash
git add app.py
```

Everything

```bash
git add .
```

---

# 💾 Commit

```bash
git commit -m "Initial commit"
```

Commit tracked files only

```bash
git commit -am "Update API"
```

---

# 📤 Push

First push

```bash
git push -u origin main
```

Later

```bash
git push
```

---

# 📥 Pull

```bash
git pull
```

Fetch only

```bash
git fetch
```

---

# 🌿 Branches

Create

```bash
git branch feature/login
```

Switch

```bash
git switch feature/login
```

Old way

```bash
git checkout feature/login
```

Create + Switch

```bash
git switch -c feature/login
```

Old way

```bash
git checkout -b feature/login
```

Delete

```bash
git branch -d feature/login
```

---

# 🔀 Merge

```bash
git merge feature/login
```

---

# 📜 Log

```bash
git log
```

Compact

```bash
git log --oneline
```

Beautiful graph

```bash
git log --graph --decorate --all --oneline
```

---

# 🔄 Undo

Discard changes

```bash
git restore app.py
```

Unstage

```bash
git restore --staged app.py
```

Undo last commit (keep changes)

```bash
git reset HEAD~1
```

Undo everything

```bash
git reset --hard HEAD
```

---

# 🎒 Stash

Save work

```bash
git stash
```

Restore

```bash
git stash pop
```

List

```bash
git stash list
```

---

# 🏷 Tags

```bash
git tag
```

Create

```bash
git tag v1.0
```

Push

```bash
git push origin --tags
```

---

# 📂 .gitignore

Ignore files like:

```text
__pycache__/
.env
.vscode/
*.pyc
```

---

# 🧹 Useful Commands

Current configuration

```bash
git config --list
```

Current user

```bash
git config user.name
```

Current email

```bash
git config user.email
```

Current remote

```bash
git remote -v
```

Current branch

```bash
git branch
```

---

# 🚀 Daily Workflow

```bash
git pull
```

↓

Edit files

↓

```bash
git status
```

↓

```bash
git add .
```

↓

```bash
git commit -m "Describe changes"
```

↓

```bash
git push
```

---

# 🔥 Common Problems

## Forgot to add files

```bash
git add .
git commit --amend
```

---

## Wrong commit message

```bash
git commit --amend -m "New message"
```

---

## See remote URL

```bash
git remote -v
```

---

## Check if using SSH

```bash
git remote -v
```

SSH looks like

```text
git@github.com:username/project.git
```

HTTPS looks like

```text
https://github.com/username/project.git
```

---

# ⭐ Commands You'll Use Every Day

```bash
git status

git add .

git commit -m "Message"

git pull

git push

git branch

git switch branch-name

git log --oneline

git stash
```

