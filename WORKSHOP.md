# 🎞️ Git Happens — Workshop Flow

**Welcome!** This workshop is hands-on. You'll break things, fix them, and learn by doing.

---

## 📋 What We'll Cover

1. **Setup** — Get Git installed and talking to GitHub
2. **Git's Mental Model** — Understand how Git thinks
3. **Your First Commit** — Create a repo from scratch
4. **Cloning** — Download this workshop repo
5. **Feature Branches** — Work without breaking main
6. **Pushing to GitHub** — Share your work
7. **Merge Conflicts** — Watch us demo (and survive)
8. **Pull Requests** — Code review workflow
9. **GitHub Issues** — Track work and bugs
10. **Team Best Practices** — Real-world tips

---

## 🧭 Section 1 – Setup & Configuration

**What:** Install Git, configure your identity, and authenticate with GitHub.

**Why:** Git needs to know who you are to label your commits. GitHub needs authentication so you can push code.

**📝 Follow along:** [Task 1: Setup & Configuration](tasks/01-setup.md)

---

## 🧱 Section 2 – Git's Mental Model

**What:** Understanding the three areas of Git.

**Why:** Before you use Git, you need to understand how it thinks.

### The Three Areas:

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│  Workspace   │───→│ Staging Area │───→│  Repository  │
│  (Your Desk) │    │ (Shopping    │    │ (Filing      │
│              │    │  Cart)       │    │  Cabinet)    │
└──────────────┘    └──────────────┘    └──────────────┘
   You edit files      git add .         git commit
```

1. **Workspace** — Your actual files where you make changes
2. **Staging Area** — Changes you've marked as "ready to save" with `git add`
3. **Repository** — Permanent history of all commits

**The flow:**
- Edit files → They're in your **workspace**
- `git add` → Moves them to **staging**
- `git commit` → Saves them to **repository** forever

**Your best friend:** `git status` (tells you which area your changes are in)

**Next:** [Task 2: Your First Commit](tasks/02-first-commit.md)

---

## 💻 Section 3 – Your First Commit

**What:** Create a Git repository from scratch and make your first commit.

**Why:** You need to understand the basics before working with existing repos.

**📝 Follow along:** [Task 2: Your First Commit](tasks/02-first-commit.md)

---

## 🌍 Section 4 – Cloning a Repository

**What:** Download this workshop repo from GitHub.

**Why:** In real life, you'll work with repos that already exist.

### Quick Commands:

```bash
git clone https://github.com/UAIS/intro-to-git-2526.git
cd intro-to-git-2526
code .
```

**What cloning gives you:**
- All the files
- All the commit history
- All the branches
- A link to the remote (origin)

**Explore:**
```bash
git log --oneline  # See commit history
git branch         # See branches
git remote -v      # See where it came from
```

**Next:** [Task 3: Feature Branches](tasks/03-feature-branches.md)

---

## 🌿 Section 5 – Feature Branches

**What:** Create a branch, make changes, and commit them.

**Why:** Professional teams never work directly on `main`. Branches keep the main codebase stable while you experiment.

### The Feature Branch Workflow:

```
1. Create a branch from main
2. Work on your feature
3. Commit your changes
4. Push to GitHub
5. Open a Pull Request
6. Get reviewed
7. Merge back to main
```

**Visual:**
```
main ──●──●──●──────────────→
            \
             ●──●──● feature-yourname
```

**📝 Follow along:** [Task 3: Feature Branches](tasks/03-feature-branches.md)

---

## ☁️ Section 6 – Pushing to GitHub

**What:** Upload your local branch to GitHub.

**Why:** Your commits are only on your computer until you push them to the cloud.

**Key concept:** `origin` is the nickname for the GitHub URL. When you push, you're sending commits from your computer to GitHub.

**📝 Follow along:** [Task 4: Pushing to GitHub](tasks/04-pushing.md)

---

## ⚔️ Section 7 – Understanding Merge Conflicts

**What:** Watch the instructors create and resolve a merge conflict live.

**Why:** Conflicts happen when two people edit the same line of code. They're scary at first, but totally normal once you understand them.

### What Causes Conflicts:

1. You edit line 5 of a file
2. Someone else edits line 5 of the **same file**
3. Git says: "I don't know which version to keep. You decide."

### Conflict Markers:

```diff
<<<<<<< HEAD
Your version of the line
=======
Their version of the line
>>>>>>> main
```

### How to Resolve:

1. Open the file
2. Decide which version to keep (or combine both)
3. Delete the markers (`<<<<<<<`, `=======`, `>>>>>>>`)
4. Save, stage, and commit

**📺 Watch the demo, then reference:** [Task 5: Understanding Merge Conflicts](tasks/05-conflicts.md)

---

## 🔍 Section 8 – Pull Requests & Code Review

**What:** Create a Pull Request to propose merging your branch into main.

**Why:** PRs enable code review, discussion, and quality control before changes go live.

### Why We Use PRs:

- **Protected main branch** — You can't push directly
- **Code review required** — At least one person must approve
- **Tests must pass** — Automated checks run
- **Main stays stable** — Production is always deployable

### The PR Workflow:

1. Push your branch to GitHub
2. Open a Pull Request on GitHub
3. Team reviews your code
4. You address feedback
5. PR gets approved and merged
6. Your branch gets deleted

**📝 Follow along:** [Task 6: Pull Requests & Code Review](tasks/06-pull-requests.md)

---

## 📋 Section 9 – GitHub Issues & Project Management

**What:** Use GitHub Issues to track bugs, features, and tasks.

**Why:** Issues help teams organize work and link commits to the problems they solve.

### Issue Workflow:

1. Create an issue describing the work
2. Create a branch to fix it
3. Make your changes
4. Open a PR with `Fixes #issue-number` in the description
5. Merge the PR → Issue auto-closes

**📝 Follow along:** [Task 7: GitHub Issues & Project Management](tasks/07-github-issues.md)

---

## 👥 Section 10 – Team Best Practices

**What:** Learn how professional teams use Git daily.

**Why:** Real-world Git is more than just commands—it's about collaboration and communication.

### Key Practices:

**Daily Workflow:**
1. `git pull origin main` (start with latest code)
2. Create a feature branch
3. Make small, focused commits
4. Push often
5. Open PRs early for feedback

**Commit Messages:**
Use conventional commits for clarity:
- `feat: add user login button`
- `fix: resolve crash on empty input`
- `docs: update readme with setup steps`

Format:
- Start lowercase
- One line, present tense
- Describe WHAT changed, not WHY (that's what PR descriptions are for)

**When Things Go Wrong:**
- **Pushed bad code?** Don't panic, talk to your team
- **Need to undo?** `git reset` for local, coordinate with team for pushed commits
- **Confused?** `git status` is your friend

**📝 Full guide:** [Task 8: Team Workflow & Best Practices](tasks/08-team-workflow.md)

---

## 🎯 Wrap-Up

**You now know:**
- ✅ Git setup and configuration
- ✅ The three-area mental model
- ✅ Creating commits and branches
- ✅ Pushing and pulling
- ✅ Handling merge conflicts
- ✅ Pull Requests and code review
- ✅ GitHub Issues for project management
- ✅ Team collaboration best practices

**Next Steps:**
- Use Git for every project
- Contribute to open source
- Check out [GitHub Skills](https://skills.github.com/) for more practice
- Join the UAIS Discord for questions

**Resources:**
- [CHEATSHEET.md](CHEATSHEET.md) — Quick command reference
- [README.md](README.md) — Repo overview
- [GitHub Docs](https://docs.github.com/) — Official documentation

---

## 🆘 Quick Troubleshooting

**Git command not found?**
- Install Git and restart your terminal

**Push failed with authentication error?**
- Run `gh auth login` to authenticate with GitHub

**Stuck in Vim?**
- Press `:q` then Enter to exit
- Set VS Code as editor: `git config --global core.editor "code --wait"`

**Made a mistake?**
- `git status` — See what state you're in
- `git log` — See your commit history
- `git merge --abort` — Cancel a merge
- Ask for help! Breaking things is how you learn.

---

**Let's Git started!** 🚀
