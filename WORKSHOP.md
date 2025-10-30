# 🎞️ Git Happens — Full Workshop Guide

**Welcome to the hands-on Git workshop!** This is your complete guide through every section. Each part has clear instructions, visuals, and things for you to type right now.

---

## 🧭 Section 1 – Welcome & Setup
Task 1: Setup & Configuration (`tasks/01-setup.md`)

### What We're Doing
Before we jump into Git magic, we need to make sure:
1. Git is installed
2. Git knows who you are
3. Your tools are ready to go

### Why This Matters
Git needs your identity to label every change you make. Think of it like signing your name on your work.

---

### ✅ Verify Git Is Installed

**Type this in your terminal:**
```bash
git --version
```

**What you should see:**  
Something like `git version 2.40.0` or similar.

**If it doesn't work:** Download Git from [git-scm.com](https://git-scm.com/downloads) and install it.

---

### 🆔 Configure Git with Your Identity

**Type these commands one by one:**

```bash
git config --global user.name "YourGitHubUsername"
git config --global user.email "youremail@users.noreply.github.com"
git config --global core.editor "code --wait"
```

**What each one does:**
- **user.name** — Your GitHub username (so commits show who made them)
- **user.email** — Your GitHub email (use the no-reply one from Settings → Emails)
- **core.editor** — Sets VS Code as your editor (saves you from Vim hell)

**Check it worked:**
```bash
git config --list
```

You should see your name and email in the output.

---

### 🎨 Visual: How Git Sees You

```
┌─────────────────┐
│  You (Developer) │
└────────┬─────────┘
         │ user.name
         │ user.email
         ↓
┌─────────────────┐       ┌──────────────┐
│  Local Repo     │  ←──→ │   GitHub     │
│  (Your Computer)│       │   (Cloud)    │
└─────────────────┘       └──────────────┘
```

Every commit you make gets tagged with your name and email.

---

### 🧭 Transition
**You're all set!** Now let's understand how Git actually thinks before we start making changes.

---

## 🧱 Section 2 – Git's Mental Model
Next hands-on: Task 2 – Your First Commit (`tasks/02-first-commit.md`)

### The Three Areas of Git

Git has **three zones** where your code lives:

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│  Workspace   │───→│ Staging Area │───→│  Repository  │
│  (Your Desk) │    │ (Shopping    │    │ (Filing      │
│              │    │  Cart)       │    │  Cabinet)    │
└──────────────┘    └──────────────┘    └──────────────┘
   You edit files      git add .         git commit
```

1. **Workspace** — Your actual files. You edit them here.
2. **Staging Area** — Changes you've marked as "ready to save."
3. **Repository** — Permanent history. Once committed, it's saved forever.

### Why Three Areas?
Because you don't always want to save *everything* at once. Maybe you fixed a bug and also changed the UI — you can commit those separately for clarity.

---

### 💻 Mini Demo: Your First Repo

**Let's make a tiny practice repo to see this in action.**

**Type this:**
```bash
mkdir git-practice
cd git-practice
git init
```

**What happened:**  
You created a folder and turned it into a Git repository. The `.git` folder is where Git stores its magic.

**Now create a file:**
```bash
echo "Hello, Git!" > hello.txt
```

**Check the status:**
```bash
git status
```

**You'll see:**  
```
Untracked files:
  hello.txt
```

This means `hello.txt` is in your **workspace** but not staged.

**Stage it:**
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

The file is now in the **staging area**.

**Commit it:**
```bash
git commit -m "feat: add hello file"
```

**Note:** We use `feat:` (Conventional Commits) to indicate this is a new feature/addition.

**Check status one more time:**
```bash
git status
```

**You'll see:**  
```
nothing to commit, working tree clean
```

The file is now in the **repository**. Saved forever!

---

### 🎨 Visual: The Three Areas in Action

```
Workspace          Staging           Repository
─────────          ───────           ──────────
hello.txt   ──┬──→ hello.txt  ──┬──→ [Commit 1]
            │                  │    "Add hello file"
         git add            git commit
```

---

### 🧭 Transition
**Nice!** You just created a repo from scratch. But in real life, you usually work with repos that already exist. Let's clone one from GitHub.

---

## 🌍 Section 3 – Cloning and Exploring
Reference section (no task) – prepares you for Task 3

### What Is Cloning?
**Cloning** means downloading a complete copy of a repository from GitHub (or anywhere) to your computer.

### How It Works

```
GitHub (Cloud)                 Your Computer
──────────────                ──────────────
┌────────────┐                ┌────────────┐
│  Repo      │  ── clone ──→  │ Local Copy │
│  (Remote)  │                │            │
└────────────┘                └────────────┘
```

When you clone, you get:
- All the files
- All the history (every commit ever made)
- All the branches

---

### 💻 Clone This Workshop Repo

**Type this:**
```bash
git clone https://github.com/UAIS/intro-to-git-2526.git
cd intro-to-git-2526
```

**Open it in VS Code:**
```bash
code .
```

**Explore the files:**  
Look at the `README.md`, the `tasks/` folder, the `practice/` folder. This is all the material for today.

**Check the history:**
```bash
git log --oneline
```

You'll see a list of commits. Each line is one saved snapshot.

**Check the remote:**
```bash
git remote -v
```

This shows where the repo came from (the GitHub URL).

---

### 🧭 Transition
**You've got the code.** Now let's make it your own by creating a branch and adding your name.

---

## 🌿 Section 4 – Feature Branches
Task 3: Feature Branches (`tasks/03-feature-branches.md`)

### What Is a Feature Branch?
A **feature branch** is a separate branch where you develop a specific feature or change without affecting the main codebase.

### Why Feature Branches?
- **Keep main stable** – Production code is always safe
- **Experiment freely** – Break things without consequences
- **Work independently** – Multiple people can work in parallel
- **Easy code review** – Changes are isolated and reviewable
- **Industry standard** – This is how professional teams work

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

---

### 🎨 Visual: Branching

```
main ──●──●──●──────────────→
            \
             ●──●──● feature-yourname
```

The main branch keeps going. Your feature branch splits off, does its thing, and can merge back later.

---

### 💻 Create Your Branch

**Type this (replace `yourname` with your actual name):**
```bash
git checkout -b feature-yourname
```

**What this does:**  
- Creates a new branch called `feature-yourname`
- Switches to that branch automatically

**Check which branch you're on:**
```bash
git branch
```

The one with the `*` is your current branch.

---

### 💻 Make a Change

**Open the file `practice/participants.txt` in VS Code.**

**Add your name at the bottom:**
```
Your Name – UAIS
```

**Save the file.**

---

### 💻 Stage and Commit

**Check what changed:**
```bash
git status
```

**Stage it:**
```bash
git add practice/participants.txt
```

**Commit it:**
```bash
git commit -m "feat: add my name to participants list"
```

**Boom.** You just made a commit on your own branch.

---

### 🧭 Transition
**Your change is saved locally.** But it's not on GitHub yet. Let's push it to the cloud.

---

## ☁️ Section 5 – Push and Pull
Task 4: Pushing to GitHub (`tasks/04-pushing.md`)

### What Is Pushing?
**Pushing** sends your local commits to GitHub so others can see them.

### What Is Pulling?
**Pulling** downloads changes from GitHub to your computer.

---

### 🎨 Visual: Push and Pull

```
Local Repo              GitHub Repo
──────────              ───────────
┌────────┐              ┌────────┐
│ Branch │ ── push ──→  │ Branch │
│        │ ←── pull ──  │        │
└────────┘              └────────┘
```

---

### 💻 Push Your Branch

**Type this:**
```bash
git push -u origin feature-yourname
```

**What this does:**
- `origin` = the GitHub repo (the remote)
- `-u` = set this branch to track the remote (you only need this once)

**Check GitHub:**  
Go to the repo on GitHub. You should see your branch listed!

---

### 💻 Pull Changes from Main

**Other people might have pushed to main. Let's get their changes.**

**Switch to main:**
```bash
git checkout main
```

**Pull the latest:**
```bash
git pull origin main
```

**What you'll see:**  
Either "Already up to date" or new commits downloading.

**Pro tip:** Always pull before you push. It prevents conflicts.

---

### 🧭 Transition
**So far, so smooth.** But what happens when two people edit the same line? Let's find out.

---

## ⚔️ Section 6 – Merge Conflicts
Task 5: Handling Merge Conflicts (`tasks/05-conflicts.md`)

### 🎭 Live Demo First!

**Instructors:** Before teaching this section, do the live conflict demo with a co-instructor!

📄 **See:** `INSTRUCTOR-DEMO.md` for the complete script

**What you'll demonstrate:**
1. Both instructors create branches
2. Both edit the same line in `practice/demo-conflict.md`
3. First instructor merges successfully
4. Second instructor gets a conflict
5. Resolve it together live on screen
6. Show the happy ending

**This takes 10-15 minutes and makes conflicts feel real and manageable.**

---

### What Is Merging?
**Merging** combines two branches. Usually it's automatic. Sometimes… it's not.

---

### 🎨 Visual: Merge

```
main       ●──●──●────────●
                 \        /
feature-yourname  ●──●──●
```

The feature branch merges back into main.

---

### 💻 Merge Your Branch (No Conflict)

**Switch to main:**
```bash
git checkout main
```

**Merge your feature branch:**
```bash
git merge feature-yourname
```

**What happens:**  
If no one else touched the same lines, Git merges automatically. You'll see "Fast-forward" or "Merge made."

---

### 💥 What About Conflicts?

**A conflict happens when:**
- You edit line 5 of a file
- Someone else edits line 5 of the same file
- You both try to merge

**Git says:** "I don't know which version to keep. You decide."

---

### 🎨 Visual: Conflict Markers

When there's a conflict, Git marks the file like this:

```diff
<<<<<<< HEAD
UAIS rocks at AI events!
=======
UAIS runs awesome AI workshops!
>>>>>>> feature-yourname
```

- `<<<<<<< HEAD` = the version on your current branch
- `=======` = separator
- `>>>>>>> feature-yourname` = the version you're trying to merge

---

### 💻 Conflict Lab

**Let's create a conflict on purpose.**

**Everyone do this:**

1. **Open `practice/conflict-demo.txt`**
2. **Edit the same line** (line 3, for example)
3. **Commit your change on your branch**
4. **Try to merge into main**

**One person will succeed. Everyone else will get a conflict.**

**To fix it:**

1. **Open the file with conflict markers**
2. **Choose which version to keep (or combine them)**
3. **Delete the markers (`<<<<<<<`, `=======`, `>>>>>>>`)**
4. **Save the file**
5. **Stage it:**
   ```bash
   git add practice/conflict-demo.txt
   ```
6. **Commit the merge:**
   ```bash
   git commit -m "fix: resolve conflict in conflict-demo.txt"
   ```
   
   **Note:** Use `fix:` for conflict resolutions since you're fixing a merge issue.

---

### 🧭 Transition
**Conflicts defeated!** Now let's learn how professional teams actually collaborate using Pull Requests and GitHub Issues.

---

## 🔍 Section 7 – Pull Requests & Code Review
Task 6: Pull Requests & Code Review (`tasks/06-pull-requests.md`)

### What's a Pull Request?
A **Pull Request (PR)** is how teams review code before merging. It's like saying: "Hey team, check out my changes before we add them to main!"

---

### 🎨 Visual: PR Workflow

```
Your Branch    →    Create PR    →    Team Reviews    →    Merge to Main
   ●──●──●            📝                  👀                    ✅
```

---

### 💻 Create Your First Pull Request

**Make sure your branch is pushed:**
```bash
git push -u origin feature-yourname
```

**On GitHub:**
1. Go to the repository page
2. You'll see a banner: **"feature-yourname had recent pushes"**
3. Click **"Compare & pull request"**

**Fill out the PR:**
- **Title:** Short summary (e.g., "Add my name to participants list")
- **Description:** What you changed and why
  ```
  ## What I Changed
  - Added my name to participants.txt
  
  ## Why
  - Part of the workshop exercise
  ```

4. Click **"Create pull request"**

---

### 👀 Code Review Process

**As a Reviewer:**

1. **Go to "Files changed" tab**
2. **Read through the code**
3. **Leave comments on specific lines** (click the `+` button)
4. **Examples of good comments:**
   - "Nice work! This looks clean."
   - "Could we add a comment here explaining what this does?"
   - "Minor: missing a period at the end"

5. **Submit your review:**
   - **Comment** = just leaving notes
   - **Approve** = looks good, ready to merge!
   - **Request changes** = needs fixes before merging

---

### 💻 Practice: Review Someone's PR

**Find a partner's PR:**
1. Go to **"Pull requests"** tab
2. Click on someone else's PR
3. Click **"Files changed"**
4. Leave at least one comment
5. Click **"Review changes"** → **"Approve"**

---

### ✅ Merging a Pull Request

**Once your PR is approved:**

1. Click **"Merge pull request"**
2. Choose merge type: **Create a merge commit** (most common)
3. Click **"Confirm merge"**
4. **Optional:** Delete your branch (keeps repo clean)

**Your changes are now in main!** 🎉

---

### 🧭 Transition
**PRs are how code gets reviewed.** But how do teams organize what to work on? Enter GitHub Issues.

---

## 📋 Section 8 – GitHub Issues & Project Management
Task 7: GitHub Issues & Project Management (`tasks/07-github-issues.md`)

### What Are GitHub Issues?

**Issues** are how teams track:
- 🐛 **Bugs** ("Login button doesn't work on mobile")
- ✨ **Features** ("Add dark mode")
- 📝 **Tasks** ("Update README")
- ❓ **Questions** ("How do we deploy this?")

Think of them as **organized to-do lists** that everyone can see.

---

### 🎨 Visual: Issue Workflow

```
Someone finds a bug
    ↓
Creates an issue
    ↓
Team discusses
    ↓
Someone takes it (assigns themselves)
    ↓
Creates a branch to fix it
    ↓
Opens a PR (references the issue)
    ↓
Merges PR → Issue auto-closes! ✅
```

---

### 💻 Create an Issue

**On GitHub:**
1. Go to **"Issues"** tab
2. Click **"New issue"**

**Fill it out:**

**Title:** Short, clear summary
```
Button color is hard to read
```

**Description:** Details, screenshots, steps to reproduce
```
## Problem
The submit button has gray text on a gray background.

## Expected
Text should be white or high contrast.

## Steps to Reproduce
1. Go to homepage
2. Scroll to contact form
3. Notice the button
```

3. **Add labels:** `bug`, `enhancement`, `help wanted`, etc.
4. **Assign** someone (or yourself)
5. Click **"Submit new issue"**

---

### 💻 Workshop Exercise: Create Your Own Issue

**For this workshop, create an issue to add your info:**

**Title:**
```
Add [Your Major] to participant info
```

**Description:**
```markdown
## What
Add my major and year to the `practice/locations.txt` file.

## Why
Workshop exercise to practice issue workflow.

## Acceptance Criteria
- [ ] Major and year added to locations.txt
- [ ] PR references this issue
- [ ] Follows format: "Major, Year"
```

**Labels:** `enhancement`, `good first issue`
**Assign:** Yourself

**Click "Submit new issue"** and note the issue number (e.g., #15)

---

### 💻 Working on an Issue

**You created issue #15 (or whatever number you got). Now let's fix it!**

**Create a branch for it:**
```bash
git checkout main
git pull origin main
git checkout -b feature/add-info-15
```

**Open `practice/locations.txt` and add your info:**
```
Computing Science, 3rd Year
```
(Use your actual major and year!)

**Commit with reference to the issue:**
```bash
git add practice/locations.txt
git commit -m "feat: add major and year to participant info

Adds my major and year to the participant info file.

Relates to #15"
```

**Push and create PR:**
```bash
git push -u origin feature/add-info-15
```

**On GitHub, create PR with:**
```markdown
## Changes
- Added my major and year to locations.txt

## Testing
- Verified format is correct (Major, Year)

Fixes #15
```

**When the PR merges, issue #15 closes automatically!** ✨

---

### 🏷️ Using Labels

Labels organize issues:

- 🐛 `bug` – Something's broken
- ✨ `enhancement` – New feature
- 📝 `documentation` – Docs need updating
- 🆘 `help wanted` – Need community help
- 🎉 `good first issue` – Easy for beginners
- ⚠️ `urgent` – Priority issue

**Add labels when creating or commenting on issues.**

---

### 💬 Issue Etiquette

**DO:**
- ✅ Be specific and clear
- ✅ Include steps to reproduce bugs
- ✅ Add screenshots when relevant
- ✅ Search existing issues first (avoid duplicates)
- ✅ Be respectful and constructive

**DON'T:**
- ❌ Write "not working" with no details
- ❌ Comment "+1" (use 👍 reaction instead)
- ❌ Demand features rudely
- ❌ Go off-topic

---

### 🧭 Transition
**You now know how to organize work with issues!** Let's wrap up with team best practices for real-world collaboration.

---

## 👥 Section 9 – Team Best Practices & Feature Branches
Task 8: Team Workflow & Best Practices (`tasks/08-team-workflow.md`)

### 🌿 Feature Branch Workflow

**This is how real teams work:**

```
main ──●──●──●────────────●──────●
          \              /      /
   feature ●──●──●──────       /
                              /
   bugfix  ──────────●──●────
```

**The Rules:**

1. **`main` is always stable** (deployable at any time)
2. **Never commit directly to `main`**
3. **Every feature/bug gets its own branch**
4. **Use descriptive branch names:**
   - ✅ `feature/user-authentication`
   - ✅ `bugfix/login-validation`
   - ✅ `docs/update-readme`
   - ❌ `fix`, `test`, `final`

5. **Open a PR for every change**
6. **Get at least one review before merging**
7. **Delete branches after merging**

---

### 💬 Commit Message Best Practices

**Good commit messages are like good documentation.**

### The Format:

```
Short summary (50 chars or less)

More detailed explanation if needed. Wrap at 72 characters.
Explain WHAT changed and WHY, not HOW (code shows how).

- Bullet points are fine
- Use present tense: "Add feature" not "Added feature"
- Reference issues: "Fixes #42"
```

**Examples:**

✅ **GOOD:**
```
Add user authentication feature

Implements JWT-based authentication for API endpoints.
Users can now register, login, and access protected routes.

Fixes #23
```

✅ **GOOD:**
```
Fix button color contrast issue

Changed submit button text from gray to white for
better readability. Meets WCAG AA standards.

Fixes #42
```

❌ **BAD:**
```
fix bug
```

❌ **BAD:**
```
update
```

---

### 🔄 Daily Team Workflow

**Every morning:**
```bash
git checkout main
git pull origin main
```

**Start a new feature:**
```bash
git checkout -b feature/my-feature
```

**Throughout the day:**
```bash
# Make changes
git add .
git commit -m "feat: add user profile page"

# Push regularly (don't lose work!)
git push -u origin feature/my-feature
```

**Before submitting PR:**
```bash
# Sync with main first
git checkout main
git pull origin main
git checkout feature/my-feature
git merge main

# Resolve any conflicts, then push
git push
```

**When done:**
- Open a Pull Request
- Request review from teammates
- Address feedback
- Merge when approved

---

### 🚨 When Things Go Wrong

**Common scenarios:**

### Someone pushed to main while you were working

```bash
git checkout main
git pull origin main
git checkout feature/my-branch
git merge main
# Fix conflicts if any
git push
```

### You committed to wrong branch

```bash
# Undo commit but keep changes
git reset --soft HEAD~1

# Switch to correct branch
git checkout correct-branch

# Commit again
git add .
git commit -m "feat: add user profile page"
```

### You accidentally pushed a bad commit

**Best practice:** If the commit is recent and no one else has pulled it yet, talk to your team first.

**If you must undo it:** Contact your team lead or instructor for help. Undoing pushed commits requires care to avoid breaking others' work.

---

### ⚡ Pro Tips for Teams

1. **Pull before you push** – Avoids conflicts
2. **Commit often** – Small commits are easier to review
3. **Push regularly** – Don't lose work
4. **Write clear PR descriptions** – Help reviewers understand
5. **Review others' code kindly** – Be constructive, not critical
6. **Use draft PRs** – For work-in-progress that needs early feedback
7. **Keep PRs small** – Easier to review, faster to merge
8. **Link PRs to issues** – Keeps everything organized
9. **Update your branch** – Merge main regularly to avoid big conflicts
10. **Communicate** – Use PR comments, issues, and team chat

---

### 🎯 What You've Mastered

- ✅ Git setup and configuration
- ✅ The three areas (workspace, staging, repository)
- ✅ Cloning, branching, committing
- ✅ Pushing and pulling
- ✅ Handling merge conflicts
- ✅ Pull requests and code review
- ✅ GitHub issues and project management
- ✅ Team collaboration best practices

---

### 📚 Keep Learning

- **Practice:** Use Git for every project, even small ones
- **Contribute:** Find an open-source project and submit a PR
- **Explore:** Try `git reflog`, `git cherry-pick`, `git bisect`
- **GitHub Skills:** [skills.github.com](https://skills.github.com/)

---

### 🎉 You Did It!

You're now dangerous with Git. Go build cool stuff, break things, and fix them with confidence.

**Questions? Stuck?** Check the [CHEATSHEET.md](./CHEATSHEET.md) or ask in the UAIS Discord.

**Happy coding!** 🚀

