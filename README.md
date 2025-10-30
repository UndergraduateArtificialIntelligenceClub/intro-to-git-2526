# 🚀 Git Happens: Learn Git by Breaking Things (and Fixing Them)

**UAIS Hands-On Git Workshop — Winter 2025-26**

Welcome! This isn't your typical "watch me code" workshop. You're going to get your hands dirty, make mistakes, break things, and learn how to fix them. Because that's how real development works.

---

## 🎯 What You'll Learn

By the end of this workshop, you'll be able to:
- **Actually understand** what Git is doing (not just copy-paste commands)
- Clone repos, create branches, and make commits like a pro
- Push and pull changes without breaking everything
- Handle merge conflicts without panicking
- Use Git in real team projects
- Recover from mistakes (because we all make them)

---

## 🛠️ Before We Start

### You'll Need:
- ✅ **Git** installed (see platform-specific instructions below)
- ✅ **VS Code** or any code editor ([get VS Code](https://code.visualstudio.com/))
- ✅ **GitHub account** ([sign up free](https://github.com/))
- ✅ **Terminal/Command Prompt** open and ready

### Installing Git

#### 🍎 macOS
**Option 1: Homebrew (recommended)**
```bash
# Install Homebrew first if you don't have it
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Then install Git
brew install git
```

**Option 2: Download Installer**
- Download from [git-scm.com/downloads](https://git-scm.com/downloads)
- Run the `.pkg` installer

**Option 3: Xcode Command Line Tools**
```bash
xcode-select --install
```

#### 🪟 Windows
**Option 1: Git for Windows (recommended)**
- Download from [git-scm.com/download/win](https://git-scm.com/download/win)
- Run the installer
- **Important:** During installation, select "Git Bash" and check "Use Git from Git Bash and also from Windows Command Prompt"

**Option 2: winget (Windows 10/11)**
```powershell
winget install --id Git.Git -e --source winget
```

**After installation, restart your terminal!**

#### 🐧 Linux
**Ubuntu/Debian:**
```bash
sudo apt update
sudo apt install git
```

**Fedora:**
```bash
sudo dnf install git
```

### Quick Setup Check:
```bash
git --version
```
If you see a version number (like `git version 2.40.0`), you're good! If not, restart your terminal and try again.

---

## 📚 Workshop Structure

We're breaking this down into bite-sized sections. Each one builds on the last, so don't skip ahead!

### **1. Setup & Configuration** 🔧
Get Git talking to GitHub with your identity.

### **2. Git's Mental Model** 🧠
Understand the three areas: Workspace → Staging → Repository.

### **3. Cloning & Exploring** 🌍
Download this repo and poke around.

### **4. Feature Branches** 🌿
Create your own branch and make changes without fear.

### **5. Push & Pull** ☁️
Share your work and sync with others.

### **6. Merge Conflicts** ⚔️
Face the beast. Defeat the beast.

### **7. Pull Requests & Code Review** 🔍
How teams review and merge code together.

### **8. GitHub Issues & Project Management** 📋
Track bugs, features, and organize teamwork.

### **9. Team Best Practices** 👥
How to collaborate without stepping on toes.

---

## 🏁 Getting Started

### Step 1: Clone This Repo
```bash
git clone https://github.com/UAIS/intro-to-git-2526.git
cd intro-to-git-2526
```

### Step 2: Configure Git
```bash
git config --global user.name "Your GitHub Username"
git config --global user.email "youremail@users.noreply.github.com"
git config --global core.editor "code --wait"
```

### Step 3: Open in VS Code
```bash
code .
```

### Step 4: Follow Along
Start with [`WORKSHOP.md`](./WORKSHOP.md) for the full guided experience, or jump into individual tasks in the [`tasks/`](./tasks/) folder.

---

## 📂 Repo Structure

```
intro-to-git-2526/
├── README.md              ← You are here
├── WORKSHOP.md            ← Full workshop slides & instructions
├── INSTRUCTOR-GUIDE.md    ← **START HERE if you're teaching this!**
├── INSTRUCTOR-DEMO.md     ← Live demo script (detailed)
├── DEMO-QUICK-REF.md      ← Quick reference for demo (print this!)
├── CHEATSHEET.md          ← Quick reference for Git commands
├── tasks/                 ← Individual exercises
│   ├── 01-setup.md
│   ├── 02-first-commit.md
│   ├── 03-feature-branches.md
│   ├── 04-pushing.md
│   ├── 05-conflicts.md
│   ├── 06-pull-requests.md
│   ├── 07-github-issues.md
│   └── 08-team-workflow.md
├── practice/              ← Files for hands-on exercises
│   ├── participants.txt
│   ├── conflict-demo.txt
│   ├── demo-conflict.md   
│   └── locations.txt      ← Add major/year (issues exercise)
└── diagrams/              ← Visual guides
    ├── git-workflow.md
    ├── branch-merge.md
    └── team-collaboration.md
```

---

## 💡 Learning Tips

- **Type every command yourself.** Don't copy-paste. Muscle memory matters.
- **Make mistakes on purpose.** Seriously. Break stuff and fix it.
- **Use `git status` constantly.** It's your best friend.
- **Read the error messages.** Git actually tells you what to do.
- **Ask questions.** There are no dumb questions in learning.

---

## 🆘 Common Issues

### "Permission denied" when pushing?
You probably need to set up SSH keys or use a personal access token. Check [GitHub's auth guide](https://docs.github.com/en/authentication).

### Stuck in Vim?
Type `:q` and hit Enter. Next time, set VS Code as your editor (we did this in setup).

---

## 🎓 After the Workshop

- Practice by contributing to open-source projects
- Check out [GitHub Skills](https://skills.github.com/) for more interactive tutorials
- Build your own projects and use Git from day one

---

## 📬 Feedback & Questions

Found a bug in this repo? Open an issue! Want to improve something? Submit a PR! (You'll know how by the end of this.)

Built with ❤️ by UAIS for the AI/dev community at UAlberta.

**Let's break some stuff and learn Git!** 🎉

