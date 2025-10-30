# Task 3: Feature Branches

**Goal:** Understand feature branches and create your own to work independently.

---

## 🌿 What's a Feature Branch?

A **feature branch** is where you develop a specific feature or change without affecting the main codebase.

```
main ──●──●──●──────────────→ (always stable)
            \
             ●──●──● feature/my-feature (your work)
```

**Why use feature branches?**
- Experiment without breaking things
- Work on multiple features in parallel
- Keep `main` always deployable
- Make code review easier
- Industry standard for team collaboration

---

## 📝 Instructions

### Step 1: Clone the Workshop Repo

If you haven't already:

```bash
git clone https://github.com/UAIS/intro-to-git-2526.git
cd intro-to-git-2526
```

---

### Step 2: Check What Branch You're On

```bash
git branch
```

You should see:
```
* main
```

The `*` shows your current branch.

---

### Step 3: Create Your Feature Branch

**Use a descriptive name that explains what you're working on:**

```bash
git checkout -b feature/add-yourname
```

**Branch naming conventions:**
- `feature/` = new feature
- `bugfix/` = fixing a bug
- `docs/` = documentation changes

**Replace `yourname` with your actual name.**

---

### Step 4: Confirm You're on Your Branch

```bash
git branch
```

**You'll see:**
```
  main
* feature/add-yourname
```

The `*` moved to your new branch!

---

### Step 5: Make a Change

Open `practice/participants.txt` in your editor.

Add your name at the bottom:

```
Your Name – UAIS – Winter 2025-26
```

**Save the file.**

---

### Step 6: Check What Changed

```bash
git status
```

You'll see:
```
On branch feature/add-yourname
Changes not staged for commit:
  modified: practice/participants.txt
```

Git knows you're on a feature branch!

---

### Step 7: Stage and Commit

```bash
git add practice/participants.txt
git commit -m "feat: add my name to participants list"
```

**Your commit message should follow Conventional Commits:**
- `feat:` for new features or additions
- `fix:` for bug fixes
- `docs:` for documentation changes
- `chore:` for maintenance tasks

**Also:**
- Be clear and specific
- Use present tense
- Start with lowercase after the prefix

---

### Step 8: View Your Branch's History

```bash
git log --oneline --graph --all
```

**You should see:**
- Your new commit on `feature/add-yourname`
- `main` branch hasn't moved
- A visual branch graph

---

### Step 9: Switch Back to Main

```bash
git checkout main
```

**Open `practice/participants.txt` again.**

**Your name is gone!** That's because your changes are on your feature branch, not main.

**Switch back:**
```bash
git checkout feature/add-yourname
```

**Your name reappears!** Each branch has its own version of the files.

---

## 🎯 Success Criteria

- [ ] Created a feature branch with your name
- [ ] Made a change to `participants.txt`
- [ ] Committed the change with a clear message
- [ ] Switched between branches and saw files change
- [ ] Understand why feature branches keep main stable

---

## 💡 Key Takeaways

- **Feature branches isolate work** from main
- **`main` stays stable** while you experiment
- **Branch names should be descriptive**
- **Each branch has its own version** of files
- **This is how professional teams work**

---

## 🌟 Real-World Example

In a real project:
```
main ─●─●─●──────────●──────→ (production code)
         \          /
  feature/login ●─●─  (Alice's work)
           \
    bugfix/typo ●─●─  (Bob's work)
```

- Alice works on login feature
- Bob fixes a typo
- Both work independently
- Main stays stable the whole time

---

## ➡️ Next Step

Your change is committed locally. Let's push it to GitHub: [Task 4: Pushing](./04-pushing.md)

