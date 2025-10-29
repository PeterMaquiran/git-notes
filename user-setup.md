# 🧾 Git User Configuration Guide

This document explains how to set your Git username and email — both **globally** (for all repositories) and **locally** (for a specific repository).  
Configuring these ensures that your commits are correctly attributed to your identity, especially when working with remote services like **Gitea**, **GitHub**, or **GitLab**.

---

## 📍 1. Global Git Configuration

Global settings apply to **all repositories** on your system.

### ➤ Set your global username and email

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### Example

```bash
git config --global user.name "Peter"
git config --global user.email "maquiranpeter29@gmail.com"
```

### ➤ Verify global configuration

```bash
git config --global user.name
git config --global user.email
```

or to view all global settings:

```bash
git config --global --list
```

### 📁 Configuration file location

Global settings are stored in:
```
~/.gitconfig
```

You can open it directly to view or edit manually.

---

## 📂 2. Local Git Configuration

Local settings apply **only to the repository** you’re currently in.  
They **override** the global configuration for that specific project.

### ➤ Set your local username and email

Inside your repository folder:
```bash
git config user.name "Your Name"
git config user.email "your@email.com"
```

### Example

```bash
git config user.name "Peter"
git config user.email "maquiranpeter29@gmail.com"
```

### ➤ Verify local configuration

```bash
git config user.name
git config user.email
```

or:
```bash
git config --list
```

### 📁 Configuration file location

Local settings are stored in:
```
<your-repo>/.git/config
```

---

## 🧪 3. Confirm Your Commit Identity

You can check how Git will identify you for new commits by running:

```bash
git config user.name
git config user.email
```

Or see a sample from your commit history:

```bash
git log --format="%h %an <%ae>" -n 5
```

---

## 🧹 4. Changing User Info on Past Commits (Optional)

If you’ve already made commits using the wrong name or email, you can rewrite them:

```bash
git filter-branch --env-filter '
export GIT_AUTHOR_NAME="Your Name"
export GIT_AUTHOR_EMAIL="your@email.com"
export GIT_COMMITTER_NAME="Your Name"
export GIT_COMMITTER_EMAIL="your@email.com"
' -- --all
```

Then force-push the updated history:
```bash
git push --force --tags origin main
```

> ⚠️ **Warning:** This rewrites commit history — only use it if you know what you’re doing or on repositories you control.

---

## ✅ 5. Summary

| Scope  | Command Example | Applies To |
|--------|-----------------|-------------|
| **Global** | `git config --global user.name "Peter"` | All repositories |
| **Local**  | `git config user.name "Peter"` | Current repository only |
| **Check config** | `git config --list` | Shows effective settings |
| **View file** | `cat ~/.gitconfig` | Global configuration file |

