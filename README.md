# Git Guide and Cheat Sheets

This repository contains comprehensive Git documentation and cheat sheets to help you master version control with Git.

## 📚 Quick Reference

### Setup and Configuration
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global core.editor "code"  # or your preferred editor
```

### Essential Commands
```bash
# Repository Management
git init                  # Initialize new repository
git clone <url>          # Clone repository
git status               # Check repository status
git add <file>           # Stage changes
git commit -m "msg"      # Commit changes
git push                 # Push to remote
git pull                 # Pull from remote

# Branching
git branch               # List branches
git branch <name>        # Create branch
git checkout <branch>    # Switch branch
git checkout -b <name>   # Create and switch
git merge <branch>       # Merge branches

# History
git log                  # View history
git log --oneline        # Compact history
git diff                 # View changes
git blame <file>         # View file history
```

### Commit Message Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

Common commit types:
| Type       | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| `feat`     | Introduces a new feature                                                    |
| `fix`      | Fixes a bug                                                                |
| `docs`     | Updates documentation                                                      |
| `style`    | Code style changes (formatting, linting, whitespace)                        |
| `refactor` | Code restructuring without changing external behavior                     |
| `test`     | Adds or modifies tests                                                     |
| `chore`    | Maintenance tasks (e.g., dependency updates, build scripts)                |
| `perf`     | Performance improvements                                                   |
| `build`    | Changes that affect the build system or external dependencies             |
| `ci`       | Changes to CI configuration or scripts                                     |
| `revert`   | Reverts a previous commit                                                 |
| `wip`      | Work in progress (temporary commit not ready for production)              |
| `hotfix`   | Quick fixes for production issues                                          |
| `deps`     | Updates or manages dependencies                                           |
| `merge`    | Merge commits from one branch to another                                   |


Examples:
```
feat(auth): add JWT authentication
fix(ui): resolve button alignment issue on mobile
refactor(database): optimize query performance
docs(readme): update installation guide
chore(deps): update dependencies to latest versions
```

### Helpful Shortcuts
```bash
# Undo Last Commit (without changes)
git reset --soft HEAD~1

# Amend Last Commit
git commit --amend -m "New message"

# View File History
git log -p <file>

# Stash Changes
git stash                # Save changes
git stash pop           # Apply and remove stash
git stash list          # List stashes
```
## 🚀 Quick Start

### Basic Git Workflow

1. **Initialize a Repository**
   ```bash
   git init                  # Create a new repository
   git clone <repo_url>      # Clone an existing repository
   ```

2. **Make Changes**
   ```bash
   git status                # Check repository status
   git add <file>            # Stage changes
   git commit -m "message"   # Commit changes
   ```

3. **Share Changes**
   ```bash
   git push                  # Push to remote repository
   git pull                  # Pull from remote repository
   ```

### Commit Message Format

Follow this structure for clear and consistent commit messages:

```
<type>(<scope>): <subject>

<body>

<footer>
```

Common commit types:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes
- `refactor`: Code restructuring
- `test`: Adding or modifying tests
- `chore`: Maintenance tasks

Example:
```
feat(auth): add JWT authentication
fix(ui): resolve button alignment issue
```

## 🔑 Key Concepts

1. **Repository (Repo)**: 
   - A directory that contains all project files and the `.git` folder
   - The `.git` folder stores all version history, configurations, and metadata
   - Can be local (on your machine) or remote (on servers like GitHub)

2. **Commit**:
   - A snapshot of your project at a specific point in time
   - Each commit has a unique SHA-1 hash (e.g., `8a7d5c3b2e1f0a9d8c7b6a5e4f3d2c1b0a9`)
   - The first 7-8 characters are usually sufficient to identify a commit
   - Contains:
     - A unique identifier (hash)
     - Author information
     - Date and time
     - Commit message
     - Reference to parent commit(s)
     - Snapshot of the entire project

3. **Branch**:
   - A separate line of development
   - Essentially a pointer to a specific commit
   - `main` (or `master`) is the default branch
   - Creating a branch is lightweight - it just creates a new pointer
   - Branches can be local or remote (e.g., `origin/main`)

4. **Staging Area (Index)**:
   - An intermediate area where you prepare changes for commit
   - Think of it as a "shopping cart" for your changes
   - Changes must be staged (`git add`) before they can be committed
   - Allows you to selectively choose which changes to commit

5. **Working Directory**:
   - The actual files you're working with
   - Contains your project files and the `.git` directory
   - Changes here are "unstaged" until you add them to the staging area

6. **HEAD**:
   - A pointer to the current commit/branch you're working on
   - Usually points to the tip of your current branch
   - Can be moved to any commit (detached HEAD state)
   - `HEAD~1` refers to the parent commit, `HEAD~2` to the grandparent, etc.

7. **Remote Repository**:
   - A copy of your repository hosted on a server (e.g., GitHub)
   - Named `origin` by default
   - Allows collaboration with other developers
   - Can have multiple remotes (e.g., `origin`, `upstream`)

8. **Git Objects**:
   - **Blobs**: Store file contents
   - **Trees**: Store directory structures and file names
   - **Commits**: Store metadata and references to trees
   - **Tags**: Store references to specific commits

## 💬 Common Commands

### Basic Operations
```bash
# Initialize and Clone
git init                    # Initialize a new repository
git clone <url>            # Clone a repository
git clone --depth 1 <url>  # Shallow clone (faster, less history)

# Check Status and Changes
git status                 # Show working directory status
git status -s              # Short status format
git diff                   # Show unstaged changes
git diff --staged         # Show staged changes
git diff HEAD            # Show all changes (staged and unstaged)

# Stage and Commit
git add <file>            # Stage specific file
git add .                 # Stage all changes
git add -p               # Interactive staging
git commit -m "msg"      # Commit with message
git commit -am "msg"     # Stage and commit in one command
```

### Branching and Merging
```bash
# Branch Management
git branch                # List local branches
git branch -r            # List remote branches
git branch -a            # List all branches
git branch <name>        # Create new branch
git branch -d <name>     # Delete branch
git branch -D <name>     # Force delete branch
git checkout <branch>    # Switch to branch
git checkout -b <name>   # Create and switch to new branch

# Merging
git merge <branch>       # Merge branch into current
git merge --no-ff <branch> # Merge with commit history
git merge --abort        # Abort merge in progress
git rebase <branch>      # Rebase current branch onto another
```

### Remote Operations
```bash
# Remote Repository
git remote -v            # List remotes
git remote add <name> <url> # Add remote
git remote show <name>   # Show remote details
git remote rename <old> <new> # Rename remote
git remote remove <name> # Remove remote

# Fetch and Pull
git fetch                # Fetch all remotes
git fetch <remote>      # Fetch specific remote
git pull                # Pull and merge
git pull --rebase      # Pull with rebase
git pull origin main   # Pull from specific branch

# Push
git push                # Push to remote
git push -u origin main # Set upstream and push
git push --force        # Force push (use with caution!)
git push --tags         # Push all tags
```

### History and Logs
```bash
# View History
git log                 # View commit history
git log --oneline      # Compact history
git log --graph        # Show branch graph
git log --stat         # Show stats
git log -p             # Show changes
git log --author="name" # Filter by author
git log --since="2 weeks ago"
git log --until="1 week ago"

# Search History
git log -S "text"      # Search for text in commits
git log -G "pattern"   # Search with regex
git blame <file>       # Show who changed what and when
```

### Stashing and Cleaning
```bash
# Stash Operations
git stash              # Stash changes
git stash save "msg"   # Stash with message
git stash list         # List stashes
git stash show         # Show stash contents
git stash apply        # Apply most recent stash
git stash pop          # Apply and remove stash
git stash drop         # Remove stash
git stash clear        # Remove all stashes

# Cleaning
git clean -n           # Show what would be cleaned
git clean -f           # Remove untracked files
git clean -fd          # Remove untracked files and directories
```

### Tagging and Releases
```bash
# Tags
git tag                # List tags
git tag <name>         # Create lightweight tag
git tag -a <name> -m "msg" # Create annotated tag
git tag -d <name>      # Delete tag
git push --tags        # Push all tags
```

### Restoring and Resetting
```bash
# Reset to a specific commit
git reset --soft <commit>  # Keep changes in staging area
git reset --mixed <commit> # Keep changes in working directory (default)
git reset --hard <commit>  # Discard all changes (use with caution!)

# Restore files to a specific state
git restore <file>         # Restore file to last commit
git restore --staged <file> # Unstage file
git restore --source=<commit> <file> # Restore file to specific commit

# Revert changes
git revert <commit>        # Create new commit that undoes changes
git revert --no-commit <commit> # Revert without committing
```

### Examples

#### 1. Working with Branches
```bash
# Create and switch to a new feature branch
git checkout -b feature/user-auth

# Make changes and commit
git add .
git commit -m "feat(auth): implement user authentication"

# Push the new branch to remote
git push -u origin feature/user-auth
```

#### 2. Merging Changes
```bash
# Merge a feature branch into main
git checkout main
git pull origin main
git merge feature/user-auth

# Resolve conflicts if any
git add .
git commit -m "merge: resolve conflicts in auth feature"

# Push changes
git push origin main
```

#### 3. Stashing Work in Progress
```bash
# Stash current changes
git stash save "WIP: working on user profile"

# Switch to another branch
git checkout hotfix/bug-123

# Fix the bug and commit
git add .
git commit -m "fix: resolve user profile display issue"

# Return to previous work
git checkout feature/user-profile
git stash pop
```

#### 4. Viewing History
```bash
# View commit history with graph
git log --graph --oneline --all

# Find commits by author
git log --author="john@example.com" --since="1 week ago"

# Search for specific changes
git log -S "password" --oneline
```

#### 5. Restoring to Previous States
```bash
# View commit history to find the target commit
git log --oneline

# Soft reset (keep changes staged)
git reset --soft HEAD~1    # Go back 1 commit, keep changes staged
git reset --soft 8a7d5c3   # Go back to specific commit

# Mixed reset (keep changes unstaged)
git reset --mixed HEAD~1   # Go back 1 commit, keep changes unstaged
git reset 8a7d5c3          # Same as above (mixed is default)

# Hard reset (discard all changes)
git reset --hard HEAD~1    # Go back 1 commit, discard all changes
git reset --hard 8a7d5c3   # Go back to specific commit

# Restore specific file to previous state
git restore --source=HEAD~1 path/to/file  # Restore file to previous commit
git restore --staged path/to/file         # Unstage file
```

#### 6. Understanding Commit References
```bash
# Different ways to reference commits
git checkout 8a7d5c3       # Using full hash
git checkout 8a7d5         # Using shortened hash
git checkout HEAD~1        # Using relative reference
git checkout main~2        # Using branch relative reference
git checkout origin/main   # Using remote branch reference

# View commit details
git show 8a7d5c3          # Show commit details
git show HEAD~1            # Show previous commit
git show main~2:file.txt   # Show file from specific commit
```

## 📋 Best Practices with Examples

### 1. Writing Clear Commit Messages

#### Good Examples:
```
feat(auth): add user login functionality
fix(ui): resolve button alignment on mobile view
docs(readme): update installation instructions
```

#### Bad Examples:
```
fixed stuff
updated code
bug fix
```

#### Detailed Commit Example:
```
feat(auth): implement JWT authentication

- Add JWT token generation
- Implement token validation middleware
- Add refresh token functionality
- Update user model to store refresh tokens

Fixes #123
```

### 2. Branch Naming Conventions

#### Good Examples:
```
feature/user-authentication
bugfix/login-error
hotfix/security-vulnerability
release/v1.2.0
```

#### Bad Examples:
```
new-feature
fix
update
```

### 3. Pull Request Best Practices

#### Good PR Title:
```
feat(auth): Add OAuth2 authentication
```

#### Good PR Description:
```
## Changes
- Implemented OAuth2 authentication flow
- Added Google and GitHub login options
- Updated user model to store OAuth tokens

## Testing
- Added unit tests for OAuth flow
- Tested with both Google and GitHub accounts

## Screenshots
[Add relevant screenshots here]

Fixes #456
```

### 4. Code Review Comments

#### Good Examples:
```
// Consider extracting this logic into a separate function
// Add error handling for network failures
// Add input validation for user email
```

#### Bad Examples:
```
// fix this
// bad code
// wrong
```

## 📊 Git Cheat Sheets

### Git Cheat Sheet - Page 1
![Git Cheat Sheet Page 1](git%20cheat%20sheet%20pages/Git%20Cheat%20Sheet%20-%20Dark%20Mode%20-%20Uncropped%20-%20Page%201%20of%204.png)

### Git Cheat Sheet - Page 2
![Git Cheat Sheet Page 2](git%20cheat%20sheet%20pages/Git%20Cheat%20Sheet%20-%20Dark%20Mode%20-%20Uncropped%20-%20Page%202%20of%204.png)

### Git Cheat Sheet - Page 3
![Git Cheat Sheet Page 3](git%20cheat%20sheet%20pages/Git%20Cheat%20Sheet%20-%20Dark%20Mode%20-%20Uncropped%20-%20Page%203%20of%204.png)

### Git Cheat Sheet - Page 4
![Git Cheat Sheet Page 4](git%20cheat%20sheet%20pages/Git%20Cheat%20Sheet%20-%20Dark%20Mode%20-%20Uncropped%20-%20Page%204%20of%204.png)

## 📄 PDF Cheat Sheets

Download comprehensive Git cheat sheets in PDF format:
- [Git Cheat Sheet - Dark Mode](Git%20Cheat%20Sheet%20-%20Dark%20Mode.pdf)
- [Git Cheat Sheet - Education](git-cheat-sheet-education.pdf)
- [Git Cheat Sheet - Standard](git-cheat-sheet.pdf)

## 🤝 Contributing

Feel free to contribute to this repository by:
1. Forking the repository
2. Creating a feature branch
3. Making your changes
4. Submitting a pull request

## 📝 License


This project is open source and available under the MIT License. 

