# Git Commands Cheat Sheet

## Basic Operations

### Clone a repository

```bash
# Clone a repository to your local machine
git clone <repository-url>
```

### Repository Status

```bash
# Check the status of your working directory
git status

# Show changes between commits, commit and working tree
git diff
```

## Branch Management

### Creating and Switching Branches

```bash
# Create a new branch
git branch <branch-name>

# Switch to a branch
git checkout <branch-name>

# Create and switch to a new branch
git checkout -b <branch-name>

# List all branches
git branch -a

# Delete a local branch (only if merged)
git branch -d <branch-name>

# Force delete a local branch (even if unmerged)
git branch -D <branch-name>

# Delete a remote branch
git push origin --delete <branch-name>

# Delete a remote branch (alternative method)
git push origin :<branch-name>
```

## Staging and Committing

### Adding Files

```bash
# Stage a specific file
git add <file-name>

# Stage all changes
git add .

# Stage all modified and deleted files (not new files)
git add -u

# Interactive staging
git add -p
```

### Commenting

```bash
# Commit with a message
git commit -m "Your commit message"

# Commit all staged changes
git commit

# Amend the most recent commit
git commit --amend

# Commit with a detailed message
git commit -m "Title" -m "Description"
```

## Remote Repository

### Managing Remotes

```bash
# Show remote repositories
git remote -v

# Add a remote repository
git remote add origin <repository-url>

# Change remote URL
git remote set-url origin <new-url>
```

### Pushing and Pulling

```bash
# Push to a branch
git push origin <branch-name>

# Force push (use with caution)
git push -f origin <branch-name>

# Pull changes from a branch
git pull origin <branch-name>

# Fetch changes without merging
git fetch
```

## Advanced Operations

### Stashing

```bash
# Stash current changes
git stash

# List all stashes
git stash list

# Apply the latest stash
git stash apply

# Apply and remove the latest stash
git stash pop

# Create a stash with a message
git stash save "Your stash message"
```

### Merging and Rebasing

```bash
# Merge a branch
git merge <branch-name>

# Rebase current branch
git rebase <branch-name>

# Interactive rebase
git rebase -i HEAD~3
```

### Logging

```bash
# View commit history
git log

# View commit history with graph
git log --graph --oneline --all

# Show commits by a specific author
git log --author="Name"
```

## Cleaning and Resetting

### Removing Untracked Files

```bash
# Dry run to see what will be deleted
git clean -n

# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd
```

### Resetting

```bash
# Unstage files
git reset <file-name>

# Reset to last commit, keeping changes
git reset HEAD~1

# Completely undo commits and changes
git reset --hard HEAD~1
```

## Useful Configurations

```bash
# Set global user name
git config --global user.name "Your Name"

# Set global email
git config --global user.email "your.email@example.com"

# Set default editor
git config --global core.editor "vim"
```

### Submodules

```bash
# Add a submodule
git submodule add <repository-url> <path>

# Update submodules
git submodule update --init --recursive
```

## Remove Accidentally Committed Files

If you have mistakenly added files or directories (like node_modules) to your Git repository, follow these steps to remove them:

### 1. Update .gitignore

```bash
# Add the directory to .gitignore
echo "node_modules/" >> .gitignore
```

### 2. Remove from Git cache

```bash
# Remove the directory from Git cache
git rm -r --cached node_modules
```

### 3. Commit the changes
```bash
# Commit the removal and updated .gitignore
git commit -m "Removed node_modules from repository"
```

### 4.Push changes
```bash
# Push the changes to the remote repository
git push origin <branch-name>
```

```text
`Note: Replace node_modules with the name of the file or directory you accidentally committed.`
```