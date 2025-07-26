
---
## Git Installation

### 🪟 Windows:

- Download from: [Link](https://git-scm.com/downloads/win)
- Use default settings, and ensure Git Bash is selected.
## 🐧 Linux:

```sh
sudo apt update
sudo apt install git
```

---
### Verify Git Installation 

```sh
git --version     
```

> Output should be something like:  `git version 2.47.1.windows.2`

### Git Configuration (first-time setup)

```sh
# Set your email
git config --global user.name "Your Name"
# Set your email (linked to your GitHub account)
git config --global user.email "your.email@example.com"
```

>To verify:
```sh
git config --list
```

# 📁 Create a Git Repository

### Create a local folder:
```sh
mkdir my-project
cd my-project
```
### Initialize Git:
```sh
git init
```
>Creates a `.git/` directory to track changes.
> Initializes a empty git repo.

### Git Workflow (Basic)
```sh
git status               # Check what's changed
git add filename         # Stage one file
git add .                # Stage all changes
git commit -m "Message"  # Save changes
git log                  # View Commit History 
```

### Connect to GitHub (SSH or HTTPS)

>Create a GitHub repo online:
> ( e.g. `https://github.com/your-username/my-project.git`)

### Connect with HTTPS:
```sh
git remote add origin https://github.com/your-username/my-project.git
```
### Or connect with SSH (recommended):
```sh
git remote add origin git@github.com:your-username/my-project.git
```

>Confirm connection:
```sh
git remove -v
```

> Pro tips :`git remote rename origin github` rename command for remote.
### Push Code to GitHub

```sh
# First time push (Setup tracking)
git push -u origin main

# Future pushes
git push 
```
`-u`          - upstream 
`origin`  - Remote Name
`main`     - Branch Name 

### Pulling and Updating

```sh
# Pull changes from Github 
git pull

# Fetch changes, then merge
git fetch && git merge
```

---
### Add-ons commands (Something detail)

```sh
# Set your default branch name (optional, e.g., 'main' instead of 'master')
git config --global init.defaultBranch main

# Set your preferred text editor (e.g., VS Code)
git config --global core.editor "code --wait"

# View all current Git configurations
git config --list
```

> Shows the remote 
```sh
git remote -v
```

> Tells our LR , who is the RR
```sh
git remote add origin
```




