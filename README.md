# 🚀 Complete Linux, Git & GitHub Reference Guide

### A comprehensive, organized reference for command-line tools, version control, and collaboration

---

## 📋 Table of Contents
1. [Linux Command Line Essentials](#linux)
2. [Git Version Control](#git)
3. [GitHub Workflows](#github)
4. [Quick Reference Cheat Sheet](#cheatsheet)
5. [Visual Mind Map](#mindmap)

---

<a id="linux"></a>
# 🐧 Linux Command Line Essentials

## 📁 File and Directory Operations

### Navigation Commands
```bash
pwd                    # Print working directory
ls                     # List directory contents
ls -la                 # List with details and hidden files
ls -lh                 # List with human-readable file sizes
cd /path/to/directory  # Change directory
cd ~                   # Go to home directory
cd ..                  # Go up one directory
cd -                   # Go to previous directory
```

### File Creation and Manipulation
```bash
touch filename         # Create empty file
mkdir dirname          # Create directory
mkdir -p path/to/dir   # Create nested directories
cp source dest         # Copy file
cp -r source dest      # Copy directory recursively
mv source dest         # Move/rename file or directory
rm filename            # Remove file
rm -r dirname          # Remove directory recursively
rm -rf dirname         # Force remove directory
rmdir dirname          # Remove empty directory
```

### File Content Operations
```bash
cat filename           # Display file content
head filename          # Show first 10 lines
head -n 20 filename    # Show first 20 lines
tail filename          # Show last 10 lines
tail -f filename       # Follow file changes in real-time
less filename          # View file with pagination
more filename          # View file page by page
wc filename            # Word, line, character count
wc -l filename         # Line count only
```

## 🔍 Search and Text Processing

### Finding Files and Content
```bash
find /path -name "pattern"     # Find files by name
find . -type f -name "*.txt"   # Find all .txt files
find . -type d -name "docs"    # Find directories named "docs"
locate filename                # Quick file location search
which command                  # Find command location
whereis command                # Find command and manual pages
```

### Text Search and Processing
```bash
grep "pattern" filename        # Search for pattern in file
grep -r "pattern" directory    # Recursive search in directory
grep -i "pattern" filename     # Case-insensitive search
grep -n "pattern" filename     # Show line numbers
grep -v "pattern" filename     # Show lines NOT matching pattern
awk '{print $1}' filename      # Print first column
sed 's/old/new/g' filename     # Replace text
sort filename                  # Sort file contents
uniq filename                  # Remove duplicate lines
cut -d',' -f1 filename         # Extract first column (CSV)
```

## 🔐 Permissions and User Management

### File Permissions
```bash
chmod 755 filename             # Set permissions (rwxr-xr-x)
chmod +x filename              # Add execute permission
chmod u+w filename             # Add write permission for user
chmod g-r filename             # Remove read permission for group
chmod o+r filename             # Add read permission for others
chown user:group filename      # Change file ownership
chown -R user:group directory  # Change ownership recursively
```

### Permission Values
| Permission | Binary | Decimal |
|------------|--------|---------|
| --- | 000 | 0 |
| --x | 001 | 1 |
| -w- | 010 | 2 |
| -wx | 011 | 3 |
| r-- | 100 | 4 |
| r-x | 101 | 5 |
| rw- | 110 | 6 |
| rwx | 111 | 7 |

### User Information
```bash
whoami                         # Current username
id                             # User and group IDs
groups                         # User's groups
w                              # Who is logged in
last                           # Last login history
su username                    # Switch user
sudo command                   # Run command as superuser
```

## ⚙️ System Information and Process Management

### System Information
```bash
uname -a                       # System information
lsb_release -a                 # Linux distribution info
df -h                          # Disk space usage
du -sh directory               # Directory size
free -h                        # Memory usage
uptime                         # System uptime
date                           # Current date and time
cal                            # Calendar
```

### Process Management
```bash
ps aux                         # List all processes
ps aux | grep process_name     # Find specific process
top                            # Real-time process monitor
htop                           # Enhanced process monitor
kill PID                       # Kill process by PID
killall process_name           # Kill process by name
jobs                           # List active jobs
bg                             # Send job to background
fg                             # Bring job to foreground
nohup command &                # Run command immune to hangups
```

### Network Commands
```bash
ping hostname                  # Test network connectivity
wget URL                       # Download file from web
curl URL                       # Transfer data from/to server
ssh user@hostname              # Secure shell login
scp file user@host:/path       # Secure copy over network
netstat -tulpn                 # Network connections
```

<a id="git"></a>
# 🎯 Git Version Control

## 🏁 Git Setup and Configuration

### Initial Setup
```bash
# Set up user identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default editor
git config --global core.editor "nano"  # or vim, code, etc.

# View all configurations
git config --list

# View specific configuration
git config user.name
```

### Repository Initialization
```bash
git init                       # Initialize new repository
git clone <repository-url>     # Clone existing repository
git clone <url> <folder-name>  # Clone to specific folder
```

## 📦 Basic Git Workflow

### Staging and Committing
```bash
# Check status
git status                     # Check repository status
git status -s                  # Short status format

# Add files to staging
git add filename               # Add specific file
git add .                      # Add all files in current directory
git add -A                     # Add all files (including deletions)
git add *.txt                  # Add all .txt files

# Commit changes
git commit -m "Commit message" # Commit with message
git commit -am "Message"       # Add and commit tracked files
git commit                     # Open editor for commit message
git commit --amend             # Modify last commit
```

### Viewing Changes and History
```bash
# View differences
git diff                       # Show unstaged changes
git diff --staged              # Show staged changes
git diff HEAD~1                # Compare with previous commit
git diff commit1..commit2      # Compare two commits

# View commit history
git log                        # Show commit history
git log --oneline              # Compact log format
git log --graph                # Show branch graph
git log --oneline --decorate --graph --all  # Detailed graph
git show <commit-hash>         # Show specific commit details
```

### File Operations
```bash
git ls-files                   # List tracked files
git rm filename                # Remove file from git and filesystem
git rm --cached filename       # Remove from git but keep file
git mv oldname newname         # Rename/move file
```

## 🌿 Branching and Merging

### Branch Management
```bash
# Create and manage branches
git branch                     # List local branches
git branch -a                  # List all branches (local + remote)
git branch branch-name         # Create new branch
git branch -d branch-name      # Delete branch (safe)
git branch -D branch-name      # Force delete branch
git branch -m old-name new-name # Rename branch

# Switch branches
git switch branch-name         # Switch to branch (Git 2.23+)
git checkout branch-name       # Switch to branch (older method)
git checkout -b branch-name    # Create and switch to branch
git switch -c branch-name      # Create and switch to branch (Git 2.23+)
```

### Merging
```bash
# Merge branches
git merge branch-name          # Merge branch into current branch
git merge --no-ff branch-name  # Force merge commit
git merge --squash branch-name # Squash merge

# Check merge status
git branch --merged            # Show merged branches
git branch --no-merged         # Show unmerged branches
```

### Rebasing
```bash
git rebase branch-name         # Rebase current branch onto branch-name
git rebase -i HEAD~3           # Interactive rebase (last 3 commits)
git rebase --continue          # Continue rebase after resolving conflicts
git rebase --abort             # Abort rebase operation
```

## 🔄 Undoing Changes

### Unstaging and Reverting
```bash
# Unstage files
git reset filename             # Unstage specific file
git reset                      # Unstage all files
git reset --hard               # Reset to last commit (lose changes)
git reset --soft HEAD~1        # Undo last commit, keep changes staged
git reset --mixed HEAD~1       # Undo last commit, unstage changes
git reset --hard HEAD~1        # Undo last commit, lose changes

# Revert commits
git revert commit-hash         # Create new commit that undoes changes
git revert HEAD                # Revert last commit

# Restore files
git restore filename           # Restore file to last committed state
git restore --staged filename  # Unstage file (Git 2.23+)
git checkout -- filename      # Restore file (older method)
```

### Stashing Changes
```bash
git stash                      # Stash current changes
git stash push -m "message"    # Stash with message
git stash list                 # List all stashes
git stash pop                  # Apply and remove latest stash
git stash apply                # Apply latest stash without removing
git stash apply stash@{2}      # Apply specific stash
git stash drop stash@{2}       # Delete specific stash
git stash clear                # Delete all stashes
```

<a id="github"></a>
# 🐙 GitHub Workflows

## 🌐 Remote Repository Management

### Working with Remotes
```bash
# View remotes
git remote                     # List remote names
git remote -v                  # List remotes with URLs
git remote show origin         # Show remote details

# Add and manage remotes
git remote add origin <url>    # Add remote repository
git remote rename origin upstream # Rename remote
git remote remove origin       # Remove remote
git remote set-url origin <new-url> # Change remote URL
```

### Push and Pull Operations
```bash
# Push changes
git push origin branch-name    # Push branch to remote
git push -u origin branch-name # Push and set upstream
git push --all origin          # Push all branches
git push --tags                # Push all tags
git push --force               # Force push (dangerous!)
git push --force-with-lease    # Safer force push

# Pull changes
git pull                       # Fetch and merge from upstream
git pull origin branch-name    # Pull specific branch
git pull --rebase              # Pull with rebase instead of merge

# Fetch changes
git fetch                      # Download objects and refs
git fetch origin               # Fetch from specific remote
git fetch --all                # Fetch from all remotes
```

## 🏷️ Tags and Releases

### Tagging
```bash
# Create tags
git tag v1.0.0                 # Create lightweight tag
git tag -a v1.0.0 -m "Version 1.0.0" # Create annotated tag
git tag -a v1.0.0 commit-hash  # Tag specific commit

# List and manage tags
git tag                        # List all tags
git tag -l "v1.*"              # List tags matching pattern
git show v1.0.0                # Show tag details
git tag -d v1.0.0              # Delete local tag
git push origin --delete v1.0.0 # Delete remote tag

# Push tags
git push origin v1.0.0         # Push specific tag
git push origin --tags         # Push all tags
```

### GitHub Specific Operations
```bash
# Fork workflow
git remote add upstream <original-repo-url>
git fetch upstream
git checkout main
git merge upstream/main

# Branch management for PRs
git checkout -b feature/new-feature
# Make changes, commit
git push -u origin feature/new-feature
# Create PR on GitHub
# After PR merge:
git checkout main
git pull origin main
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

## 🔧 Advanced Git Features

### Git Aliases
```bash
# Create useful aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.graph 'log --oneline --decorate --graph --all'

# Usage: git st instead of git status
```

### Git Hooks
```bash
# Hook locations
ls .git/hooks/                 # View available hooks

# Common hooks:
# - pre-commit: Run before commit
# - post-commit: Run after commit
# - pre-push: Run before push
# - post-receive: Run after receiving push
```

### Submodules
```bash
# Add submodule
git submodule add <repository-url> <path>

# Initialize and update submodules
git submodule init
git submodule update
git submodule update --recursive

# Clone repository with submodules
git clone --recursive <repository-url>
```

<a id="cheatsheet"></a>
# 📄 Quick Reference Cheat Sheet

## 🚀 Most Used Commands

| Category | Command | Description |
|----------|---------|-------------|
| **Linux Basics** | `pwd` | Show current directory |
| | `ls -la` | List files with details |
| | `cd directory` | Change directory |
| | `mkdir dirname` | Create directory |
| | `rm -rf dirname` | Remove directory |
| | `chmod 755 file` | Set file permissions |
| **Git Basics** | `git status` | Check repository status |
| | `git add .` | Stage all changes |
| | `git commit -m "msg"` | Commit with message |
| | `git push origin main` | Push to remote |
| | `git pull` | Pull latest changes |
| **Git Branching** | `git branch` | List branches |
| | `git switch -c branch` | Create and switch branch |
| | `git merge branch` | Merge branch |
| | `git branch -d branch` | Delete branch |
| **Git Undo** | `git reset filename` | Unstage file |
| | `git restore filename` | Restore file |
| | `git revert HEAD` | Revert last commit |
| | `git stash` | Temporarily save changes |

## 🎯 Git Workflow Pattern

```bash
# 1. Start new feature
git switch -c feature/new-feature

# 2. Make changes and commit
git add .
git commit -m "Add new feature"

# 3. Push to remote
git push -u origin feature/new-feature

# 4. Create Pull Request on GitHub

# 5. After merge, cleanup
git switch main
git pull origin main
git branch -d feature/new-feature
```

<a id="mindmap"></a>
# 🧠 Visual Mind Map

## 🌳 Linux, Git & GitHub Knowledge Tree

```md
📚 LINUX, GIT & GITHUB MASTERY
|
├── 🐧 LINUX COMMAND LINE
│   ├── 📁 File Operations
│   │   ├── Navigation      (pwd, ls, cd)
│   │   ├── Creation        (touch, mkdir)
│   │   ├── Manipulation    (cp, mv, rm)
│   │   └── Content         (cat, head, tail, less)
|   |
│   ├── 🔍 Search & Text
│   │   ├── Find Files      (find, locate, which)
│   │   ├── Search Content  (grep, awk, sed)
│   │   └── Process Text    (sort, uniq, cut)
|   |
│   ├── 🔐 Permissions
│   │   ├── File Permission (chmod)
│   │   ├── Ownership       (chown)
│   │   └── User Management (whoami, su, sudo)
|   |
│   └── ⚙️ System
│       ├── Info            (uname, df, free, uptime)
│       ├── Processes       (ps, top, kill)
│       └── Network         (ping, wget, ssh)
│
├── 🎯 GIT VERSION CONTROL
│   ├── 🏁 Setup
│   │   ├── Config          (git config)
│   │   ├── Init            (git init)
│   │   └── Clone           (git clone)
|   |
│   ├── 📦 Basic Workflow
│   │   ├── Status          (git status)
│   │   ├── Staging         (git add)
│   │   ├── Committing      (git commit)
│   │   └── History         (git log, git diff)
|   |
│   ├── 🌿 Branching
│   │   ├── Create          (git branch, git switch)
│   │   ├── Merge           (git merge)
│   │   ├── Rebase          (git rebase)
│   │   └── Delete          (git branch -d)
|   |
│   ├── 🔄 Undoing
│   │   ├── Reset           (git reset)
│   │   ├── Revert          (git revert)
│   │   ├── Restore         (git restore)
│   │   └── Stash           (git stash)
|   |
│   └── 🔧 Advanced
│       ├── Aliases
│       ├── Hooks
│       └── Submodules
│
└── 🐙 GITHUB WORKFLOWS
    ├── 🌐 Remotes
    │   ├── Add/Manage (git remote)
    │   ├── Push            (git push)
    │   ├── Pull            (git pull)
    │   └── Fetch           (git fetch)
    |   
    ├── 🏷️ Tags & Releases
    │   ├── Create Tags     (git tag)
    │   ├── Push Tags
    │   └── GitHub Releases
    |   
    └── 🔄 Collaboration
        ├── Fork Workflow
        ├── Pull Requests
        ├── Code Review
        └── Issue Tracking
```

## 🛤️ Learning Roadmap

### 🎯 Beginner Path (1-2 weeks)
1. **Linux Basics**
   - Master navigation (`pwd`, `ls`, `cd`)
   - Learn file operations (`touch`, `mkdir`, `cp`, `mv`, `rm`)
   - Understand basic permissions (`chmod`, `chown`)

2. **Git Fundamentals**
   - Setup Git (`git config`)
   - Learn basic workflow (`init`, `add`, `commit`, `status`)
   - Understand history (`git log`, `git diff`)

3. **GitHub Basics**
   - Create account and first repository
   - Learn push/pull (`git push`, `git pull`)
   - Clone existing repositories

### 🚀 Intermediate Path (2-4 weeks)
1. **Advanced Linux**
   - Master text processing (`grep`, `awk`, `sed`)
   - Learn system monitoring (`ps`, `top`, `netstat`)
   - Understand pipes and redirection

2. **Git Branching**
   - Create and switch branches (`git branch`, `git switch`)
   - Merge strategies (`git merge`, `git rebase`)
   - Resolve conflicts

3. **GitHub Collaboration**
   - Fork repositories
   - Create Pull Requests
   - Code review process

### 🏆 Advanced Path (1-2 months)
1. **Linux Mastery**
   - Shell scripting
   - Process management
   - Network troubleshooting

2. **Git Advanced**
   - Interactive rebase
   - Git hooks
   - Submodules

3. **GitHub Enterprise**
   - GitHub Actions (CI/CD)
   - Issue tracking
   - Project management

---

## 💡 Pro Tips

### 🔥 Linux Power Tips
- Use `history | grep command` to find previously used commands
- Create aliases for frequently used commands: `alias ll='ls -la'`
- Use `ctrl+r` for reverse search in command history
- Master tab completion for faster typing

### ⚡ Git Power Tips
- Use `git commit --amend` to fix the last commit message
- Create meaningful commit messages (what and why)
- Use `git stash` when switching contexts quickly
- Set up aliases for commonly used Git commands

### 🌟 GitHub Power Tips
- Use issue templates for consistent reporting
- Set up branch protection rules
- Use GitHub CLI (`gh`) for command-line GitHub operations
- Enable GitHub Pages for project documentation

---

## 📚 Additional Resources

- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [Linux Command Reference](https://man7.org/linux/man-pages/)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)

---

*🎉 Happy Learning! Remember: Practice makes perfect. Start with the basics and gradually build up your skills.*