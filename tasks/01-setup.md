# Task 1: Setup & Configuration

**Goal:** Get Git installed and talking to GitHub.

---

## ✅ What You'll Do

1. Verify Git is installed
2. Configure your identity
3. Set VS Code as your default editor

---

## 📝 Instructions

### Step 1: Install Git (Platform-Specific)

#### 🍎 macOS

**Option 1: Homebrew (Recommended)**
```bash
# Install Homebrew first if you don't have it
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Then install Git
brew install git
```

**Option 2: Download Installer**
- Go to [git-scm.com/download/mac](https://git-scm.com/download/mac)
- Download the `.pkg` installer
- Run it and follow the prompts

**Option 3: Xcode Command Line Tools**
```bash
xcode-select --install
```

#### 🪟 Windows

**Option 1: Git for Windows (Recommended)**
1. Go to [git-scm.com/download/win](https://git-scm.com/download/win)
2. Download the installer
3. Run it
4. **Important settings during installation:**
   - Select "Git Bash" as the terminal
   - Choose "Use Git from Git Bash and also from Windows Command Prompt"
   - Select "Checkout Windows-style, commit Unix-style line endings"
   - Use default for everything else

**Option 2: winget (Windows 10/11)**
```powershell
winget install --id Git.Git -e --source winget
```

**After installation: Restart your terminal!**

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

---

### Step 2: Verify Installation

Open your terminal and type:

```bash
git --version
```

**Expected output:** Something like `git version 2.40.0` or higher

**If it still fails:** Restart your terminal and try again

---

### Step 3: Configure Your Identity

Git needs to know who you are for every commit. Run these commands one by one:

```bash
git config --global user.name "YourGitHubUsername"
git config --global user.email "youremail@users.noreply.github.com"
git config --global core.editor "code --wait"
```

**Replace:**
- `YourGitHubUsername` with your actual GitHub username
- `youremail@users.noreply.github.com` with your GitHub no-reply email (find it in GitHub Settings → Emails)

---

### Step 4: Verify Configuration

```bash
git config --list
```

You should see your `user.name`, `user.email`, and `core.editor` in the output.

---

## 🎯 Success Criteria

- [ ] `git --version` shows a version number
- [ ] `git config --list` shows your correct name and email
- [ ] VS Code is set as your editor

---

## 🆘 Troubleshooting

**Git not found?**  
Make sure you installed Git and restarted your terminal.

**Email not working?**  
Check that the email matches one in your GitHub account (Settings → Emails).

**Stuck in Vim?**  
Type `:q` and press Enter. Then set VS Code as your editor.

---

## ➡️ Next Step

Once configured, move on to [Task 2: Your First Commit](./02-first-commit.md)

