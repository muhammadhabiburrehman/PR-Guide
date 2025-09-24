# PR-Guide
# Git Workflow Guide - From Clone to PR

## Complete Step-by-Step Process

### Step 1: Clone the Project
```bash
git clone <repository-url>
cd <project-folder>
```

### Step 2: Fetch All Remote Branches
```bash
git fetch origin
```
*This downloads all remote branches to your local repository*

### Step 3: Check Available Branches
```bash
# Check local branches
git branch

# Check remote branches  
git branch -r

# Check both local and remote branches
git branch -a
```

### Step 4: Create Local Branch from Remote Dev Branch
```bash
git checkout -b dev origin/dev
```
*This creates a local `dev` branch that tracks the remote `dev` branch*

### Step 4.1: Verify You Have Latest Code
```bash
git pull origin dev
```
*This ensures your local branch has the most recent code from remote dev*

### Step 4.2: Check if Local and Remote are in Sync
```bash
git status
```
*Should show "Your branch is up to date with 'origin/dev'"*

**If there's a mismatch, sync with:**
```bash
git fetch origin
git reset --hard origin/dev
```
*⚠️ Warning: This will overwrite local changes. Use with caution!*

### Step 5: Create Your Feature Branch
```bash
git checkout -b feature/your-feature-name
```
*Create a new branch for your specific task from dev*

### Step 6: Do Your Work/Tasks
- Write code
- Make changes
- Test your work

### Step 7: Check Status
```bash
git status
```
*See what files have been modified, added, or deleted*

### Step 8: Stage Changes
```bash
git add .
```
*Stages all changes. You can also stage specific files: `git add filename.ext`*

### Step 9: Commit Changes
```bash
git commit -m "Descriptive commit message about what you did"
```

### Step 10: Push Your Branch (First Time)
```bash
git push -u origin feature/your-feature-name
```
*The `-u` flag sets up tracking. After this, you can just use `git push`*

### Step 11: Create Pull Request
- Go to your repository on GitHub/GitLab/Bitbucket
- Click "Create Pull Request" or "Merge Request"
- Set base branch to `dev`
- Set compare branch to your `feature/your-feature-name`
- Add description and submit

## Quick Commands Reference

### Daily Workflow Commands
```bash
# Switch to dev and get latest changes
git checkout dev
git pull origin dev

# Create new feature branch
git checkout -b feature/new-task

# After making changes
git add .
git commit -m "Your message"
git push  # (after first push with -u)
```

### Useful Check Commands
```bash
git status          # Check current status
git log --oneline   # See commit history
git branch          # See current branch
git remote -v       # Check remote URLs
```

### Emergency Commands
```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Discard local changes and match remote
git fetch origin
git reset --hard origin/<branch-name>

# See differences
git diff            # Changes not staged
git diff --staged   # Changes staged for commit
```

## Branch Naming Conventions
- `feature/login-system`
- `bugfix/header-alignment`
- `hotfix/critical-security-issue`
- `chore/update-dependencies`

## Best Practices

1. **Always work on feature branches**, never directly on `main` or `dev`
2. **Pull latest changes** from dev before starting new work
3. **Write clear commit messages** that explain what and why
4. **Keep commits small and focused** - one feature per commit when possible
5. **Test your code** before committing
6. **Regular pushes** - don't wait days to push your work

## Troubleshooting

### "Your branch is behind origin/dev"
```bash
git pull origin dev
```

### "Merge conflicts"
1. Open conflicted files
2. Resolve conflicts manually
3. `git add .`
4. `git commit -m "Resolve merge conflicts"`

### "Permission denied"
- Check your SSH keys or use HTTPS with token
- Verify you have write access to the repository

---

**Remember**: When in doubt, `git status` is your friend! It tells you exactly what state your repository is in.
