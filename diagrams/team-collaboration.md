# 👥 Team Collaboration Workflow

Visual guides for working with teams using Git and GitHub.

---

## 🔄 Complete Team Workflow

```
┌─────────────────────────────────────────────────────────────┐
│                    GITHUB (Remote)                          │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐ │
│  │  main branch (always stable)                          │ │
│  │  ●──●──●────────●────────●──────→                     │ │
│  └───────────────────────────────────────────────────────┘ │
│                                                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │ feature/login│  │ bugfix/typo  │  │ feature/dark │     │
│  │ (Alice)      │  │ (Bob)        │  │ (Charlie)    │     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Pull Requests (Code Review)                         │  │
│  │  - PR #45: Login feature (Alice)                     │  │
│  │  - PR #46: Fix typo (Bob) ✅ Approved                │  │
│  │  - PR #47: Dark mode (Charlie) 💬 In review         │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Issues (Task Tracking)                              │  │
│  │  🐛 #42: Button color issue (Assigned: Bob)          │  │
│  │  ✨ #43: Add user profiles (Assigned: Alice)         │  │
│  │  📝 #44: Update README (Open)                        │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                              │
                              │ git clone
                              │ git pull
                              │ git push
                              ↓
┌─────────────────────────────────────────────────────────────┐
│                  LOCAL COMPUTERS                            │
│                                                             │
│  Alice's Computer    Bob's Computer    Charlie's Computer  │
│  ┌──────────────┐   ┌──────────────┐   ┌──────────────┐   │
│  │ main         │   │ main         │   │ main         │   │
│  │ feature/login│   │ bugfix/typo  │   │ feature/dark │   │
│  └──────────────┘   └──────────────┘   └──────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

---

## 🌿 Feature Branch Workflow (Step by Step)

### Day 1: Alice Starts a Feature

```
GitHub:
main ──●──●──●
         ↑
      everyone's work

Alice's Computer:
1. git checkout main
2. git pull origin main
3. git checkout -b feature/login

   main ──●──●──●
            \
    feature/login (Alice working here)
```

---

### Day 2: Alice Makes Progress, Bob Fixes a Bug

```
Alice's Computer:
feature/login ──●──●  (commits)
                ↓
         git push origin feature/login
                ↓
GitHub:
main ──●──●──●
         \
  feature/login ──●──● (Alice's work)

Bob's Computer:
1. git checkout main
2. git pull origin main
3. git checkout -b bugfix/typo
4. Makes fix
5. git push origin bugfix/typo

GitHub:
main ──●──●──●
         \    \
  feature/   bugfix/typo ──● (Bob's work)
  login ──●──●
```

---

### Day 3: Bob Opens PR, Gets Reviewed, Merges

```
GitHub:
1. Bob creates PR for bugfix/typo
2. Alice reviews it → Approves ✅
3. Bob merges PR

main ──●──●──●──●  ← Bob's fix merged!
         \
  feature/login ──●──●  (Alice still working)
```

---

### Day 4: Alice Updates Her Branch, Completes Feature

```
Alice's Computer:
1. git checkout main
2. git pull origin main  ← Gets Bob's fix!
3. git checkout feature/login
4. git merge main  ← Brings Bob's fix into her branch

   main ──●──●──●──●
            \      \
    feature/login ──●──●──●  ← Now has Bob's fix too

5. Finishes feature
6. git push origin feature/login
7. Opens PR on GitHub
```

---

## 🔍 Pull Request Workflow

```
Developer              Team                  Main Branch
─────────            ──────               ──────────────

   │                    │                      │
   │  1. Push branch    │                      │
   │───────────────────→│                      │
   │                    │                      │
   │  2. Create PR      │                      │
   │───────────────────→│                      │
   │                    │                      │
   │                    │  3. Review code      │
   │                    │  👀                  │
   │                    │  - Leave comments    │
   │                    │  - Request changes   │
   │                    │  - Or approve ✅     │
   │                    │                      │
   │  4. Address        │                      │
   │     feedback       │                      │
   │───────────────────→│                      │
   │                    │                      │
   │                    │  5. Final approval   │
   │                    │  ✅                  │
   │                    │                      │
   │                    │  6. Merge PR         │
   │                    │─────────────────────→│
   │                    │                      │
   │                    │                   ✨ Code
   │                    │                   in main!
```

---

## 📋 Issue-to-PR Workflow

```
1. Someone creates an issue
   ┌──────────────────────────┐
   │ Issue #42                │
   │ 🐛 Bug: Button broken    │
   │ Status: Open             │
   └──────────────────────────┘
            ↓
2. Developer claims it
   ┌──────────────────────────┐
   │ Issue #42                │
   │ 🐛 Bug: Button broken    │
   │ Assigned: Alice          │
   └──────────────────────────┘
            ↓
3. Create branch
   git checkout -b bugfix/button-42
            ↓
4. Make fixes & commit
   git commit -m "Fix button

   Resolves #42"
            ↓
5. Push & create PR
   ┌──────────────────────────┐
   │ PR #45                   │
   │ Fix button issue         │
   │ Fixes #42                │
   └──────────────────────────┘
            ↓
6. Code review
   👀 Review → ✅ Approve
            ↓
7. Merge PR
   ┌──────────────────────────┐
   │ PR #45                   │
   │ ✅ Merged                │
   └──────────────────────────┘
            ↓
8. Issue auto-closes!
   ┌──────────────────────────┐
   │ Issue #42                │
   │ ✅ Closed via PR #45     │
   └──────────────────────────┘
```

---

## ⚔️ Merge Conflict Resolution (Team Scenario)

### Scenario: Alice and Bob edit the same file

**Alice's changes:**
```javascript
// config.js
const API_URL = 'https://api-v2.example.com';
```

**Bob's changes:**
```javascript
// config.js
const API_URL = 'https://api.example.com/v2';
```

**Both pushed their branches. Bob merges first:**
```
main ──●──●──●──●  ← Bob's change merged
         \
  Alice's ──●──●
```

**Alice tries to merge:**
```bash
git checkout main
git pull origin main
git checkout feature/alice
git merge main
```

**Git says:** 🚨 CONFLICT!

**Alice sees:**
```javascript
// config.js
<<<<<<< HEAD
const API_URL = 'https://api-v2.example.com';
=======
const API_URL = 'https://api.example.com/v2';
>>>>>>> main
```

**Alice's decision process:**
1. Talks to Bob: "Which URL is correct?"
2. They agree on Bob's format
3. Alice edits:
```javascript
// config.js
const API_URL = 'https://api.example.com/v2';
```

4. Resolves:
```bash
git add config.js
git commit -m "Resolve conflict, use Bob's URL format"
git push
```

**Lesson:** Communication prevents conflicts!

---

## 🔄 Daily Team Synchronization

```
Morning Routine (Everyone does this):
┌─────────────────────────────────┐
│ git checkout main               │
│ git pull origin main            │
│ ← Get everyone's merged work   │
└─────────────────────────────────┘
           ↓
Work on Your Branch:
┌─────────────────────────────────┐
│ git checkout feature/my-work    │
│ ... make changes ...            │
│ git add .                       │
│ git commit -m "Clear message"   │
│ git push                        │
└─────────────────────────────────┘
           ↓
Before Creating PR:
┌─────────────────────────────────┐
│ git checkout main               │
│ git pull origin main            │
│ git checkout feature/my-work    │
│ git merge main                  │
│ ← Make sure you're up to date  │
└─────────────────────────────────┘
           ↓
Create PR → Get Reviews → Merge
           ↓
After Merge:
┌─────────────────────────────────┐
│ git checkout main               │
│ git pull origin main            │
│ git branch -d feature/my-work   │
│ ← Clean up                      │
└─────────────────────────────────┘
```

---

## 🛡️ Protected Main Branch

```
Developer tries to push to main directly:
┌──────────────────────────────────┐
│ $ git push origin main           │
│                                  │
│ ❌ ERROR!                        │
│ Branch main is protected.        │
│ You must use a Pull Request.    │
└──────────────────────────────────┘

Instead, developer must:
┌──────────────────────────────────┐
│ 1. Create feature branch         │
│ 2. Push feature branch           │
│ 3. Open Pull Request             │
│ 4. Get review & approval         │
│ 5. Then merge via GitHub         │
└──────────────────────────────────┘

Benefits:
✅ Code is always reviewed
✅ Tests run automatically
✅ No accidental force pushes
✅ Main stays stable
✅ Team has visibility
```

---

## 📊 Branch Lifecycle

```
┌─────────┐
│  START  │
└────┬────┘
     │
     ↓
┌──────────────────┐
│ Create branch    │ git checkout -b feature/X
│ from main        │
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ Work & commit    │ git commit -m "..."
│ (repeat)         │
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ Push to GitHub   │ git push -u origin feature/X
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ Open Pull        │ Create PR on GitHub
│ Request          │
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ Code Review      │ Teammates review
│                  │ Request changes or approve
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ Address feedback │ More commits if needed
│ (if needed)      │
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ PR approved ✅   │ At least 1 approval
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ Merge to main    │ Click "Merge" on GitHub
└────┬─────────────┘
     │
     ↓
┌──────────────────┐
│ Delete branch    │ Cleanup (optional but recommended)
└────┬─────────────┘
     │
     ↓
┌─────────┐
│   END   │
└─────────┘
```

---

## 🎯 Communication Best Practices

### Before You Start Work:
```
1. Check GitHub Issues
   "Is anyone else working on this?"

2. Comment on issue
   "I'll take this!"

3. Assign yourself
   Click "Assignees" → Your name

4. Create branch
   git checkout -b feature/description
```

### While Working:
```
1. Push regularly
   "Don't lose work!"

2. Update PR description
   "Keep team informed"

3. Ask questions
   "Hey team, should we use API v1 or v2?"
```

### During Code Review:
```
1. Be responsive
   "Reply within 24 hours"

2. Ask for clarification
   "Can you explain why you'd prefer X?"

3. Thank reviewers
   "Thanks for catching that!"
```

---

## 💡 Team Success Tips

1. **Pull main every morning** – Stay in sync
2. **Small, frequent commits** – Easier to review and merge
3. **Descriptive branch names** – Everyone knows what you're working on
4. **Clear PR descriptions** – Help reviewers understand
5. **Link PRs to issues** – Keep work organized
6. **Review others' code** – Learn and help the team
7. **Keep PRs small** – Under 400 lines if possible
8. **Test before pushing** – Don't break the build
9. **Communicate** – Use PR comments, issues, and chat
10. **Be kind** – Code review is about the code, not the person

---

**Remember:** Git and GitHub are tools for collaboration. The goal is to help your team ship great software together! 🚀

