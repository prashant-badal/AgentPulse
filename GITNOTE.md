## Git Note 

# Git & GitHub — Basic Learning Notes

## 1. Git vs GitHub

* **Git** → Tool installed on my PC to track code changes.
* **GitHub** → Online platform where Git repositories are stored.
* Git works locally; GitHub is the remote location.


PC → Git → Local Repository → GitHub


---

## 2. Check Git Installation


git --version

If it shows a version, Git is installed.



## 3. Configure Git Identity

Tell Git who I am:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Check:

```bash
git config --global user.name
git config --global user.email


**Note:** This identifies my commits. It does not authenticate me with GitHub.

---

## 4. Clone a GitHub Repository

If a project already exists on GitHub:

```bash
git clone <github-repository-url>
```

Example:

```bash
git clone https://github.com/username/project.git
```

Then:

```bash
cd project
```

### What `git clone` does

```text
GitHub Repository
       ↓
    git clone
       ↓
My PC
```

It downloads the project and its Git history.

---

## 5. Check Git Repository

Inside the project:

```bash
git status
```

This tells me:

* Current branch
* Changed files
* Whether there are changes to commit

---

## 6. Check GitHub Connection

```bash
git remote -v
```

Example:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

### Meaning

`origin` = nickname for the GitHub repository.


Local Project
      ↓
    origin
      ↓
GitHub Repository
```

`fetch` → GitHub → PC

`push` → PC → GitHub

---

# 7. Basic Git Workflow

After changing code:

### Step 1 — Check changes

```bash
git status
```

### Step 2 — Stage changes

```bash
git add .
```

`git add .` means: prepare all changed files for commit.

### Step 3 — Commit

```bash
git commit -m "Describe the change"
```

Commit = save the change in my **local Git history**.

### Step 4 — Push

```bash
git push origin main
```

Push = upload my committed changes from PC to GitHub.

---

# 8. Main Git Flow

```text
Write / Change Code
        ↓
   git status
        ↓
     git add .
        ↓
 git commit -m "message"
        ↓
   git push origin main
        ↓
      GitHub
```

---

# 9. Important Commands

| Command                   | Purpose                        |
| ------------------------- | ------------------------------ |
| `git --version`           | Check Git installation         |
| `git clone URL`           | Download GitHub project to PC  |
| `git status`              | Check current changes/status   |
| `git remote -v`           | Check GitHub remote connection |
| `git add .`               | Stage changes                  |
| `git commit -m "message"` | Save changes locally           |
| `git push origin main`    | Upload changes to GitHub       |
| `git pull`                | Get latest changes from GitHub |
| `git log`                 | View commit history            |

---

# 10. Authentication Problem I Faced

When I ran:

```bash
git push origin main
```

I got:

```text
Authentication failed
```

and later:

```text
403 Permission denied
```

### Important understanding

My remote URL was correct:

```text
https://github.com/prashant-badal/AgentPulse.git
```

But GitHub authentication was the problem.

GitHub does **not** use the normal GitHub account password for HTTPS Git operations.

For HTTPS authentication, use a:

**Personal Access Token (PAT)**

```text
Username → GitHub username
Password → Personal Access Token
```

The token needs permission to write to the repository.

---

# 11. Windows Credential Manager

Windows can save GitHub login credentials.

Find it:

```text
Windows Start
→ Search "Credential Manager"
→ Windows Credentials
→ Generic Credentials
```

If an old/wrong GitHub credential is saved, it can cause authentication problems.

Removing the GitHub credential forces Git to ask for authentication again.

**Removing the credential does NOT delete the GitHub account or repository.**

---

# 12. Current Understanding

```text
Git installed
     ↓
Configure Git identity
     ↓
Clone repository
     ↓
Local Git repository
     ↓
Check remote
     ↓
Make code changes
     ↓
git add .
     ↓
git commit
     ↓
Authenticate with GitHub
     ↓
git push
     ↓
GitHub
```

### Most important concept

**Git tracks and manages my code locally.**

**GitHub stores/shares the remote repository.**

**`commit` saves locally.**

**`push` sends commits to GitHub.**

**`pull` brings changes from GitHub to my PC.**
