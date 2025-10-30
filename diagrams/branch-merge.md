# 🌿 Branching and Merging Visuals

Deep dive into how branches and merges work in Git.

---

## 📌 What Is a Branch?

A branch is a **pointer** to a commit. That's it!

```
main    ──●──●──●  ← Branch 'main' points here
             ↑
          HEAD (you are here)
```

When you create a new branch, you're just creating a new pointer:

```
main    ──●──●──●  ← main
             ↑
          feature  ← new pointer!
             ↑
          HEAD
```

---

## 🔀 Creating and Switching Branches

### Before: On main

```
main    ──●──●──●
             ↑
          HEAD
```

### After: `git checkout -b feature`

```
main    ──●──●──●
             ↑
          feature
             ↑
          HEAD (switched)
```

Both branches point to the same commit (for now).

---

## ➕ Making Commits on a Branch

### Make a commit on `feature`:

```
main    ──●──●──●
             \
              ●  ← feature (moved forward)
              ↑
           HEAD
```

Now `feature` points to a new commit. `main` stayed where it was.

### Another commit:

```
main    ──●──●──●
             \
              ●──●  ← feature
                 ↑
              HEAD
```

---

## 🔁 Fast-Forward Merge

If `main` hasn't changed, merging is simple:

### Before merge:

```
main    ──●──●──●
             \
              ●──●  ← feature
                 ↑
              HEAD
```

### After `git checkout main` then `git merge feature`:

```
main    ──●──●──●──●──●  ← main moved forward (fast-forward)
                    ↑
                 HEAD
```

Git just moved the `main` pointer forward. No merge commit needed!

---

## 🔀 Three-Way Merge

If both branches have new commits, Git creates a merge commit:

### Before merge:

```
main    ──●──●──●──●  ← main has new commits
             \
              ●──●  ← feature has different commits
```

### After `git merge feature`:

```
main    ──●──●──●──●────●  ← merge commit
             \          /
              ●────●───
                feature
```

The merge commit has **two parents**: one from `main`, one from `feature`.

---

## ⚔️ Merge Conflicts

Conflicts happen when **both branches edit the same line**.

### Example:

**On `main`:**
```python
# line 5
print("Hello from main")
```

**On `feature`:**
```python
# line 5
print("Hello from feature")
```

**After merge attempt:**

```diff
<<<<<<< HEAD
print("Hello from main")
=======
print("Hello from feature")
>>>>>>> feature
```

**You must choose:**
1. Keep main's version
2. Keep feature's version
3. Combine both
4. Write something completely new

**After you fix it:**
```python
print("Hello from main and feature")
```

Then:
```bash
git add file.py
git commit -m "Resolve conflict"
```

---

## 🪄 Rebase (Alternative to Merge)

Rebase **replays** your commits on top of another branch.

### Before rebase:

```
main    ──●──●──●──M  ← main has new commits
             \
              ●──F1──F2  ← feature
```

### After `git rebase main`:

```
main    ──●──●──●──M──F1'──F2'  ← feature commits replayed
                        ↑
                     feature
```

Notice:
- No merge commit
- Linear history
- Commits `F1` and `F2` are **rewritten** (new hashes)

---

## 🆚 Merge vs Rebase

| Aspect | Merge | Rebase |
|--------|-------|--------|
| **History** | Shows true timeline | Linear, cleaner |
| **Commits** | Preserves original | Rewrites commits |
| **Conflicts** | Resolve once | May resolve multiple times |
| **Use when** | Shared branches | Personal branches |
| **Safety** | Safer (no rewrite) | Dangerous if pushed |

**Golden Rule:** Never rebase public/shared branches!

---

## 🔄 Rebase Workflow

### Step 1: Update main

```bash
git checkout main
git pull origin main
```

### Step 2: Rebase your feature

```bash
git checkout feature
git rebase main
```

### Step 3: Handle conflicts (if any)

```bash
# Fix conflicts in files
git add .
git rebase --continue
```

### Step 4: Force push (if already pushed)

```bash
git push --force-with-lease origin feature
```

---

## 📋 Branch Strategies

### Feature Branch Workflow

```
main ──●──●──●──────────●──────●
          \            /      /
   feature ●──●──●────       /
                            /
   bugfix  ──────────●──●──
```

**Rules:**
- `main` is always stable
- Each feature/bugfix gets its own branch
- Merge via Pull Request after review

---

### Common Branch Names

- `main` or `master` – production code
- `develop` – integration branch
- `feature/login` – new feature
- `bugfix/typo` – bug fix
- `hotfix/security` – urgent fix
- `yourname/experiment` – personal experiment

---

## 🧪 Practical Examples

### Example 1: New Feature

```bash
git checkout main
git pull origin main
git checkout -b feature/dark-mode
# ... make changes ...
git add .
git commit -m "Add dark mode toggle"
git push origin feature/dark-mode
# Open PR on GitHub
```

### Example 2: Fix a Bug

```bash
git checkout main
git pull origin main
git checkout -b bugfix/header-alignment
# ... fix bug ...
git add .
git commit -m "Fix header alignment issue"
git push origin bugfix/header-alignment
# Open PR
```

### Example 3: Update Your Branch

```bash
git checkout main
git pull origin main
git checkout feature/dark-mode
git merge main
# or
git rebase main
```

---

## 🎯 Quick Commands

| Task | Command |
|------|---------|
| List branches | `git branch` |
| List all branches (including remote) | `git branch -a` |
| Create branch | `git branch feature-name` |
| Create and switch | `git checkout -b feature-name` |
| Switch branch | `git checkout branch-name` |
| Rename current branch | `git branch -m new-name` |
| Delete branch | `git branch -d branch-name` |
| Force delete | `git branch -D branch-name` |
| Merge branch into current | `git merge branch-name` |
| Rebase current onto branch | `git rebase branch-name` |
| Abort merge | `git merge --abort` |
| Abort rebase | `git rebase --abort` |

---

## 💡 Pro Tips

1. **Use descriptive branch names:** `feature/user-authentication` not `fix`
2. **Keep branches short-lived:** Merge within days, not weeks
3. **Pull before pushing:** Avoid conflicts
4. **Delete merged branches:** Keep repo clean
5. **Use `git log --graph --all --oneline`** to visualize branches

---

**Remember:** Branches are cheap! Don't be afraid to create them. Experiment, break things, and learn.

