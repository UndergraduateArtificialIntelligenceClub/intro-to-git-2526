# Task 4: Pushing to GitHub

**Goal:** Share your local changes with the world (or at least GitHub).

---

## ☁️ What's Pushing?

**Pushing** uploads your local commits to a remote repository (GitHub).

```
Local Repo              GitHub Repo
──────────              ───────────
┌────────┐              ┌────────┐
│ Branch │ ── push ──→  │ Branch │
└────────┘              └────────┘
```

---

## 📝 Instructions

### Step 1: Verify Your Remote

```bash
git remote -v
```

You should see:
```
origin  https://github.com/UAIS/intro-to-git-2526.git (fetch)
origin  https://github.com/UAIS/intro-to-git-2526.git (push)
```

`origin` is the default name for the remote repo.

---

### Step 2: Push Your Branch

Make sure you're on your feature branch:

```bash
git branch
```

**Make sure your last commit used conventional commits:**
```bash
git log --oneline  # Check your commit message
```

If not, you can amend it:
```bash
git commit --amend -m "feat: add my name to participants list"
```

**Then push:**

```bash
git push -u origin feature-yourname
```

**What this does:**
- `origin` = the GitHub repo
- `feature-yourname` = your branch name
- `-u` = set upstream tracking (so future pushes can just be `git push`)

---

### Step 3: Check GitHub

Go to the repo on GitHub: `https://github.com/UAIS/intro-to-git-2526`

You should see a banner saying:

```
feature-yourname had recent pushes
[Compare & pull request]
```

**Don't click it yet!** We'll make a pull request later.

---

### Step 4: Pull Changes from Main

Other people might have pushed changes to main. Let's get them.

**Switch to main:**
```bash
git checkout main
```

**Pull the latest:**
```bash
git pull origin main
```

**What you'll see:**
- "Already up to date" (if no changes)
- Or a list of new commits

---

### Step 5: Merge Main into Your Branch (Optional)

If main changed, you might want to update your branch:

**Switch back to your branch:**
```bash
git checkout feature-yourname
```

**Merge main into your branch:**
```bash
git merge main
```

This brings the latest changes from main into your branch.

---

## 🎯 Success Criteria

- [ ] Pushed your branch to GitHub
- [ ] Saw your branch appear on GitHub
- [ ] Pulled latest changes from main
- [ ] (Optional) Merged main into your branch

---

## 💡 Key Takeaways

- `git push` sends commits to GitHub
- `-u origin branchname` sets tracking for future pushes
- `git pull` downloads changes from GitHub
- Always pull before you push to avoid conflicts

---

## ➡️ Next Step

Time to face the scariest part of Git: [Task 5: Merge Conflicts](./05-conflicts.md) 😱

