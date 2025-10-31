# Task 2: Your First Commit

**Goal:** Understand Git's three areas by creating a repo from scratch.

---

## 🧠 The Three Areas

Before we start, remember:

```
Workspace       →    Staging Area    →    Repository
(You edit)           (git add)            (git commit)
```

1. **Workspace:** Your actual files
2. **Staging Area:** Changes marked as "ready to commit"
3. **Repository:** Permanent saved history

---

## 📝 Instructions

### Step 1: Create a Practice Repo

```bash
mkdir git-practice
cd git-practice
git init
```

**What happened:** You created a new Git repository. The `.git` folder stores all the magic.

---

### Step 2: Create a File

```bash
echo "Hello, Git!" > hello.txt
```

---

### Step 3: Check the Status

```bash
git status
```

**You'll see:**
```
Untracked files:
  hello.txt
```

This means `hello.txt` is in your **workspace** but Git isn't tracking it yet.

---

### Step 4: Stage the File

```bash
git add hello.txt
```

**Check status again:**
```bash
git status
```

**Now it says:**
```
Changes to be committed:
  new file: hello.txt
```

The file is in the **staging area**.

---

### Step 5: Commit the File

```bash
git commit -m "feat: add hello file"
```

**What `-m` does:** Adds a commit message inline (so you don't open an editor).

**Notice the `feat:` prefix?** This is called **Conventional Commits** - a standard way to write commit messages:
- `feat:` = new feature
- `fix:` = bug fix
- `docs:` = documentation change
- `chore:` = maintenance task

**Check status one more time:**
```bash
git status
```

**You'll see:**
```
nothing to commit, working tree clean
```

The file is now in the **repository**!

---

### Step 6: View the History

```bash
git log
```

You'll see your commit with:
- Commit hash (unique ID)
- Author (you!)
- Date
- Message

**Pro tip:** Use `git log --oneline` for a compact view.

---

## 🎯 Success Criteria

- [ ] Created a repo with `git init`
- [ ] Created a file and saw it as "untracked"
- [ ] Staged the file with `git add`
- [ ] Committed the file with `git commit`
- [ ] Saw your commit in `git log`

---

## 💡 Key Takeaways

- **Workspace → Staging → Repository** is the Git flow
- `git status` is your best friend (use it constantly!)
- Commits are permanent snapshots

---

## ➡️ Next Step

Now that you understand the basics, let's clone a real repo: [Task 3: Feature Branches](./03-feature-branches.md)

