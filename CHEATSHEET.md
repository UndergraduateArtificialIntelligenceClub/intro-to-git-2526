# 📄 Git Cheatsheet

Quick reference for common Git commands. Bookmark this!

---

## 🚀 Getting Started

| Command | What It Does |
|---------|-------------|
| `git --version` | Check if Git is installed |
| `git config --global user.name "Name"` | Set your name |
| `git config --global user.email "email"` | Set your email |
| `git config --list` | View all settings |
| `git init` | Create a new Git repo in current folder |
| `git clone <url>` | Download a repo from GitHub |

---

## 📊 Checking Status

| Command | What It Does |
|---------|-------------|
| `git status` | See what changed (use this constantly!) |
| `git log` | View commit history |
| `git log --oneline` | Compact history |
| `git log --graph --all --oneline` | Visual branch history |
| `git diff` | See unstaged changes |
| `git diff --staged` | See staged changes |
| `git show <hash>` | View a specific commit |

---

## 📝 Making Changes

| Command | What It Does |
|---------|-------------|
| `git add <file>` | Stage a specific file |
| `git add .` | Stage all changes |
| `git add -p` | Stage changes interactively |
| `git commit -m "message"` | Commit staged changes |
| `git commit -am "message"` | Stage and commit all tracked files |
| `git commit --amend` | Edit the last commit |

---

## 🌿 Branching

| Command | What It Does |
|---------|-------------|
| `git branch` | List all branches |
| `git branch <name>` | Create a new branch |
| `git checkout <branch>` | Switch to a branch |
| `git checkout -b <name>` | Create and switch to new branch |
| `git switch <branch>` | Switch branches (newer syntax) |
| `git switch -c <name>` | Create and switch (newer syntax) |
| `git branch -d <name>` | Delete a merged branch |
| `git branch -D <name>` | Force delete a branch |
| `git branch -m <new-name>` | Rename current branch |

---

## 🔀 Merging

| Command | What It Does |
|---------|-------------|
| `git merge <branch>` | Merge a branch into current branch |
| `git merge --abort` | Cancel a merge in progress |
| `git merge --no-ff <branch>` | Force a merge commit (no fast-forward) |

---

## 🌐 Working with Remotes

| Command | What It Does |
|---------|-------------|
| `git remote -v` | List remote repos |
| `git remote add origin <url>` | Add a remote |
| `git push origin <branch>` | Push branch to remote |
| `git push -u origin <branch>` | Push and set upstream tracking |
| `git push --force-with-lease` | Force push (safer than `--force`) |
| `git pull origin <branch>` | Download and merge changes |
| `git fetch origin` | Download changes without merging |

---

## 💾 Stashing

| Command | What It Does |
|---------|-------------|
| `git stash` | Save current changes temporarily |
| `git stash save "message"` | Save with a description |
| `git stash list` | View all stashes |
| `git stash pop` | Apply and delete latest stash |
| `git stash apply` | Apply but keep stash |
| `git stash drop` | Delete latest stash |
| `git stash clear` | Delete all stashes |

---

## ⏪ Undoing Things

| Command | What It Does |
|---------|-------------|
| `git restore <file>` | Discard unstaged changes in file |
| `git restore --staged <file>` | Unstage a file |
| `git reset <file>` | Unstage a file (older syntax) |
| `git reset --soft HEAD~1` | Undo last commit, keep changes staged |
| `git reset --mixed HEAD~1` | Undo last commit, keep changes unstaged |
| `git reset --hard HEAD~1` | Undo last commit, discard changes ⚠️ |
| `git clean -fd` | Delete untracked files (careful!) |

---

---

## 🔍 Searching and Finding

| Command | What It Does |
|---------|-------------|
| `git grep "text"` | Search for text in tracked files |
| `git log --grep="text"` | Search commit messages |
| `git log -S "text"` | Search for text in commit contents |
| `git blame <file>` | See who changed each line |
| `git bisect start` | Start binary search for bug |

---

## 🆘 Emergency Commands

| Command | What It Does |
|---------|-------------|
| `git reflog` | View all recent actions (time travel!) |
| `git reset --hard <hash>` | Go back to a specific commit |
| `git cherry-pick <hash>` | Copy a specific commit to current branch |
| `git fsck` | Check repository for corruption |

---

## ⚙️ Configuration

| Command | What It Does |
|---------|-------------|
| `git config --global core.editor "code --wait"` | Set VS Code as editor |
| `git config --global init.defaultBranch main` | Use `main` instead of `master` |
| `git config --global pull.rebase false` | Default merge on pull |
| `git config --global alias.st status` | Create alias `git st` |

---

## 🎯 Common Workflows

### Starting a New Feature

```bash
git checkout main
git pull origin main
git checkout -b feature/new-feature
# ... make changes ...
git add .
git commit -m "Add new feature"
git push -u origin feature/new-feature
```

### Updating Your Branch

```bash
git checkout main
git pull origin main
git checkout feature/my-branch
git merge main
```

### Fixing a Merge Conflict

```bash
# After merge conflict appears:
# 1. Open conflicted files
# 2. Edit to resolve conflicts
# 3. Remove conflict markers
git add .
git commit -m "Resolve merge conflict"
```

### Syncing a Fork

```bash
git remote add upstream <original-repo-url>
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

---

## 🧠 Git Concepts Quick Reference

### The Three Areas

```
Workspace → Staging → Repository
  edit       add       commit
```

### File States

```
Untracked → Modified → Staged → Committed
```

### Remote vs Local

- **Local:** Your computer
- **Remote:** GitHub/GitLab (usually called `origin`)
- **Upstream:** Original repo (if you forked)

---

## 💡 Best Practices

✅ **DO:**
- Commit often with clear messages
- Pull before pushing
- Use branches for features
- Write descriptive commit messages
- Review changes before committing (`git diff`)

❌ **DON'T:**
- Commit directly to `main` (use branches!)
- Force push to shared branches
- Commit large binary files
- Write vague messages like "fix bug"
- Ignore `.gitignore`

---

## 📚 Commit Message Format (Conventional Commits)

### Format: `type: description`

**Common types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation
- `style:` - Formatting (no logic change)
- `refactor:` - Code refactoring
- `test:` - Tests
- `chore:` - Maintenance
- `perf:` - Performance

### Good Examples:
```
feat: add user authentication system
fix: resolve login validation timeout
docs: update README with setup instructions
refactor: simplify database connection logic
chore: upgrade dependencies to latest versions
```

### Bad Examples:
```
fixed stuff                     ← No type, vague
update                         ← No type, no context
Add new feature                ← No type, wrong case
feat: Added authentication     ← Wrong tense (should be "add")
final version                  ← Not descriptive
```

### Full Example:
```
feat: add password reset functionality

Implements email-based password reset:
- Send reset email with token
- Token expires after 1 hour
- Secure password update flow

Fixes #42
```

---

## 🎨 Helpful Aliases

Add these to your `~/.gitconfig`:

```ini
[alias]
    st = status
    co = checkout
    br = branch
    ci = commit
    unstage = restore --staged
    last = log -1 HEAD
    visual = log --oneline --graph --all
    undo = reset --soft HEAD~1
```

**Use them like:**
```bash
git st        # same as git status
git visual    # pretty branch graph
git undo      # undo last commit
```

---

## 🆘 Common Problems and Solutions

### Problem: Committed to wrong branch

```bash
git log  # copy the commit hash
git checkout correct-branch
git cherry-pick <hash>
git checkout wrong-branch
git reset --hard HEAD~1
```

### Problem: Accidentally deleted file

```bash
git checkout HEAD <file>
# or
git restore <file>
```

### Problem: Want to undo last commit but keep changes

```bash
git reset --soft HEAD~1
```

### Problem: Want to undo last commit and discard changes

```bash
git reset --hard HEAD~1
```

### Problem: Pushed sensitive data

```bash
# Remove file from history (nuclear option)
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch <file>" \
  --prune-empty --tag-name-filter cat -- --all

git push --force
```

Then change any exposed credentials immediately!

---

## 🎓 Learning Resources

- **Official Git Docs:** [git-scm.com/doc](https://git-scm.com/doc)
- **GitHub Skills:** [skills.github.com](https://skills.github.com/)
- **Git Visualizer:** [git-school.github.io/visualizing-git](https://git-school.github.io/visualizing-git/)
- **Oh Shit, Git!?!:** [ohshitgit.com](https://ohshitgit.com/) (real talk about fixing mistakes)

---

## 🚀 Pro Tips

1. **Use `git status` constantly** — it tells you what to do next
2. **Read error messages** — Git is surprisingly helpful
3. **Commit early, commit often** — small commits are easier to manage
4. **Write meaningful commit messages** — future you will thank you
5. **When in doubt, make a branch** — branches are free!
6. **Use `git reflog` for emergencies** — it's your safety net
7. **Test before you commit** — make sure code works

---

**Keep this handy and happy Git-ing!** 🎉

---

*Last updated: Winter 2025-26 | UAIS Workshop*

