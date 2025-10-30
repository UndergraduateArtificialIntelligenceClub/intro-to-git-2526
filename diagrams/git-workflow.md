# 🎨 Git Workflow Diagrams

Visual guides to help you understand how Git works.

---

## 📦 The Three Areas of Git

```
┌─────────────────────┐
│                     │
│   WORKSPACE         │  ← You edit files here
│   (Working Tree)    │
│                     │
└──────────┬──────────┘
           │
           │ git add
           ↓
┌─────────────────────┐
│                     │
│   STAGING AREA      │  ← Changes ready to commit
│   (Index)           │
│                     │
└──────────┬──────────┘
           │
           │ git commit
           ↓
┌─────────────────────┐
│                     │
│   REPOSITORY        │  ← Permanent history
│   (.git directory)  │
│                     │
└─────────────────────┘
```

**Think of it like:**
- **Workspace** = Your desk (messy, in progress)
- **Staging Area** = Your shopping cart (selected items)
- **Repository** = Your receipt (permanent record)

---

## 🌿 Branch Workflow

```
main ──●──●──●──────────────●──────→
            \              /
             \            / (merge)
              \          /
   feature     ●───●───●
```

### How It Works:

1. **Branch off** from main to work on a feature
2. **Make commits** on your branch
3. **Merge** back to main when done

### Commands:

```bash
git checkout -b feature-branch  # Create and switch to branch
git checkout main               # Switch back to main
git merge feature-branch        # Merge feature into main
```

---

## ☁️ Local vs Remote

```
┌─────────────────────────────────┐
│      YOUR COMPUTER (Local)      │
│                                 │
│  ┌──────────────────────────┐  │
│  │  Workspace               │  │
│  │  ┌──────────────────┐    │  │
│  │  │  Staging Area    │    │  │
│  │  │  ┌────────────┐  │    │  │
│  │  │  │ Repository │  │    │  │
│  │  │  └────────────┘  │    │  │
│  │  └──────────────────┘    │  │
│  └──────────────────────────┘  │
│                                 │
└────────────┬────────────────────┘
             │
             │ git push
             │
             ↓
┌─────────────────────────────────┐
│      GITHUB (Remote)            │
│                                 │
│  ┌──────────────────────────┐  │
│  │  Repository (origin)     │  │
│  │  - main                  │  │
│  │  - feature-branch        │  │
│  │  - other branches        │  │
│  └──────────────────────────┘  │
│                                 │
└─────────────────────────────────┘
             │
             │ git pull
             │
             ↓
       Other developers
```

**Key Points:**
- **Local** = on your computer
- **Remote** = on GitHub (or GitLab, etc.)
- **`git push`** = send changes from local to remote
- **`git pull`** = download changes from remote to local

---

## 🔄 Complete Development Cycle

```
1. Clone repo
   ↓
┌──────────────────────────────┐
│  git clone [url]             │
└───────────┬──────────────────┘
            ↓
2. Create branch
   ↓
┌──────────────────────────────┐
│  git checkout -b feature     │
└───────────┬──────────────────┘
            ↓
3. Make changes
   ↓
┌──────────────────────────────┐
│  Edit files in workspace     │
└───────────┬──────────────────┘
            ↓
4. Stage changes
   ↓
┌──────────────────────────────┐
│  git add .                   │
└───────────┬──────────────────┘
            ↓
5. Commit changes
   ↓
┌──────────────────────────────┐
│  git commit -m "message"     │
└───────────┬──────────────────┘
            ↓
6. Push to GitHub
   ↓
┌──────────────────────────────┐
│  git push origin feature     │
└───────────┬──────────────────┘
            ↓
7. Create Pull Request
   ↓
┌──────────────────────────────┐
│  On GitHub: New PR           │
└───────────┬──────────────────┘
            ↓
8. Review & Merge
   ↓
┌──────────────────────────────┐
│  Merge PR into main          │
└──────────────────────────────┘
```

---

## 📊 File States

```
Untracked ──→ Unmodified ──→ Modified ──→ Staged
   ↑            │              │            │
   │            │              │            │
   │            │ edit file    │            │
   │            └──────────────┘            │
   │                                        │
   │                 git add                │
   └────────────────────────────────────────┘
                   git commit
```

**State Meanings:**
- **Untracked**: Git doesn't know about this file
- **Unmodified**: File is in repo, no changes since last commit
- **Modified**: File changed but not staged
- **Staged**: Changes marked for next commit

---

## 🎯 Quick Reference

| What You Want | Command |
|--------------|---------|
| See status | `git status` |
| Stage a file | `git add filename` |
| Stage all changes | `git add .` |
| Commit | `git commit -m "message"` |
| Push | `git push origin branch-name` |
| Pull | `git pull origin branch-name` |
| Create branch | `git checkout -b branch-name` |
| Switch branch | `git checkout branch-name` |
| Merge | `git merge branch-name` |

---

**Pro Tip:** Keep a terminal window open with `git status` ready. It's your best friend for knowing where you are!

