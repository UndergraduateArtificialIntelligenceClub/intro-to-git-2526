# Task 1: Setup & Configuration

**Goal:** Get Git installed and talking to GitHub.

Before you can collaborate on code, you need Git to identify you and connect to GitHub. Think of this as setting up your developer ID card.

---

## ✅ What You'll Do

1. Verify Git is installed
2. Configure your identity
3. Set VS Code as your default editor
4. Authenticate with GitHub CLI

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
- `youremail@users.noreply.github.com` with your GitHub no-reply email

**Important:** Your email must match one of the verified emails in your GitHub account (Settings → Emails). This ensures your commits are properly attributed to you on GitHub.

**If `code --wait` fails:**
```bash
# The 'code' command isn't in your PATH yet
# Open VS Code → Command Palette (Cmd/Ctrl + Shift + P)
# Type: "Shell Command: Install 'code' command in PATH"
# Then run the git config command again
```

---

### Step 4: Verify Configuration

```bash
git config --list
```

You should see your `user.name`, `user.email`, and `core.editor` in the output.

---

### Step 5: Authenticate GitHub CLI (for push/pull access)

**Why do this?** Pushing to and pulling from GitHub requires authentication. The easiest way is using GitHub CLI.

**First, make sure you have a GitHub account!**  
If you don't have one yet: [https://github.com/join](https://github.com/join)

#### Install GitHub CLI:

**macOS:**
```bash
brew install gh
```

**Windows:**
```powershell
winget install --id GitHub.cli
```

**Linux:**
```bash
# Ubuntu/Debian
sudo apt install gh

# Fedora
sudo dnf install gh
```

#### Authenticate:

```bash
gh auth login
```

**Follow the prompts:**
1. What account: **GitHub.com**
2. Protocol: **HTTPS**
3. Authenticate: **Login with a web browser** (easiest!)
4. Copy the one-time code shown
5. Press Enter to open browser
6. Paste the code and authorize

**Test it worked:**
```bash
gh auth status
```

You should see: `✓ Logged in to github.com`

**Bonus:** This saves your auth, so Git can push/pull automatically! Plus `gh` has cool commands like `gh pr create` we'll use later.

---

## 🎯 Success Criteria

- [ ] `git --version` shows a version number
- [ ] `git config --list` shows your correct name and email
- [ ] VS Code is set as your editor
- [ ] `gh auth status` shows you're logged in

**✅ You're now fully set up!** Next, you'll make your first Git commit and see the three-area workflow in action.

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

