# Task 7: GitHub Issues & Project Management

**Goal:** Learn how teams track bugs, features, and tasks using GitHub Issues.

---

## 📋 What Are GitHub Issues?

**Issues** are like organized to-do lists for your project. Teams use them to track:

- 🐛 **Bugs** – "Submit button doesn't work on mobile"
- ✨ **Features** – "Add user profile page"
- 📝 **Tasks** – "Update documentation"
- ❓ **Questions** – "Which database should we use?"
- 💡 **Ideas** – "What if we added dark mode?"

---

## 🎨 The Issue-to-PR Workflow

```
1. Someone creates an issue
2. Team discusses it
3. Someone claims it (assigns themselves)
4. Create a branch to work on it
5. Make changes and commit
6. Open PR that references the issue
7. Merge PR → Issue auto-closes! ✅
```

---

## 📝 Instructions

### Step 1: Browse Existing Issues

**Go to the repository on GitHub:**
1. Click the **"Issues"** tab
2. Look at open issues

**You'll see:**
- Issue titles
- Labels (bug, enhancement, etc.)
- Who created it and when
- Number of comments

---

### Step 2: Create an Issue

**Click "New issue"**

**Fill it out well:**

**Title:** Be specific and clear (50 chars or less)

✅ **GOOD:**
```
Add pronunciation guide to README
```

❌ **BAD:**
```
Fix thing
```

**Description:** Give details, context, and examples

**Template for bugs:**
```markdown
## Problem
Describe what's broken or not working.

## Expected Behavior
What should happen instead?

## Steps to Reproduce
1. Go to homepage
2. Click submit button
3. See error message

## Environment
- Browser: Chrome 120
- OS: macOS 14

## Screenshots
[attach if relevant]
```

**Template for features:**
```markdown
## Feature Request
What do you want added?

## Why
Explain the use case.

## Proposed Solution
How might this work?

## Alternatives
Other ways to solve this?
```

---

### Step 3: Practice – Create a Real Issue

**For this workshop, create an issue:**

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

**Add labels:**
- Click the gear icon next to "Labels"
- Select: `enhancement`, `good first issue`

**Assign yourself:**
- Click gear next to "Assignees"
- Select your username

**Click "Submit new issue"**

---

### Step 4: Work on the Issue

**Now you have an issue! Let's fix it.**

**Note the issue number** (e.g., #15)

**Create a branch for it:**
```bash
git checkout main
git pull origin main
git checkout -b feature/add-info-15
```

**Notice the branch name includes the issue number!**

---

### Step 5: Make the Change

**Open `practice/locations.txt`:**

Add your major and year in this format:
```
Your Major, Year
```

Example:
```
Computing Science, 3rd Year
```

---

### Step 6: Commit with Reference to Issue

```bash
git add practice/locations.txt
git commit -m "feat: add major and year to participant info

Adds my major and year to the participant info file as part of workshop.

Relates to #15"
```

**Notice:** 
- We used `feat:` prefix (conventional commits)
- We mentioned `#15` (the issue number) in the commit message

---

### Step 7: Push and Create PR

```bash
git push -u origin feature/add-info-15
```

**On GitHub, create a PR with this description:**

```markdown
## Changes
- Added my major and year to locations.txt

## Testing
- Verified format is correct (Major, Year)
- Information is accurate

Fixes #15
```

**The magic words:** `Fixes #15`

This tells GitHub: "When this PR merges, close issue #15 automatically."

---

### Step 8: Watch the Magic

**Look at your PR:**
- Scroll down to see a reference to issue #15
- Click it to jump to the issue

**Look at your issue:**
- You should see a reference to your PR
- GitHub linked them!

**When you merge the PR:**
- Issue #15 will auto-close
- It'll say "Closed via #(PR number)"

---

## 🏷️ Using Labels Effectively

**Common labels and when to use them:**

| Label | When to Use |
|-------|------------|
| `bug` | Something doesn't work |
| `enhancement` | New feature request |
| `documentation` | Docs need updating |
| `good first issue` | Easy for beginners |
| `help wanted` | Need community help |
| `question` | Discussion needed |
| `wontfix` | Not going to address this |
| `duplicate` | Already reported |
| `urgent` | High priority |

**Add labels to your issues to organize them!**

---

## 💬 Issue Etiquette (How to Be a Good Community Member)

### DO:

✅ **Be specific and detailed**
```
Bad:  "Not working"
Good: "Login fails when password contains special characters"
```

✅ **Include reproduction steps**

✅ **Search before creating** (avoid duplicates)

✅ **Add screenshots/error messages**

✅ **Be respectful and constructive**

✅ **Follow up if you solve it yourself**
```
"Solved by updating to version 2.0. Closing."
```

### DON'T:

❌ **Be vague or demanding**
```
"This sucks, fix it NOW"
```

❌ **Comment "+1"** – use 👍 reaction instead

❌ **Spam or go off-topic**

❌ **Open duplicate issues**

---

## 🎯 Success Criteria

- [ ] Created a well-written issue with title, description, and labels
- [ ] Assigned the issue to yourself
- [ ] Created a branch to work on it
- [ ] Made changes and committed
- [ ] Opened a PR that references the issue with `Fixes #number`
- [ ] Merged PR and watched issue auto-close

---

## 💡 Key Takeaways

- **Issues organize work** into trackable tasks
- **Good issues are specific** and detailed
- **Labels help categorize** issues
- **Reference issues in commits** with `#number`
- **Use `Fixes #number` in PRs** to auto-close issues
- **Issues create transparency** – everyone knows what's being worked on

---

## 🌟 Real-World Example

**Issue #42: Button color has poor contrast**

Created by: Sarah  
Labels: `bug`, `accessibility`, `good first issue`  
Assigned to: Alex

**Description:**
```markdown
## Problem
Submit button on the contact form has gray text on gray background.
Hard to read, fails WCAG AA standards.

## Expected
Button text should be white or high-contrast.

## Steps to Reproduce
1. Go to /contact
2. Scroll to form
3. Notice submit button

## Screenshot
[image showing low contrast]

## Suggested Fix
Change button text color to white (#FFFFFF).
```

**Alex's workflow:**
```bash
git checkout -b bugfix/button-contrast-42
# Make changes
git commit -m "Fix submit button contrast

Changed text color from #666 to #FFF for better
accessibility. Now meets WCAG AA standards.

Fixes #42"
git push -u origin bugfix/button-contrast-42
# Opens PR, references issue
# PR merges, issue auto-closes
```

---

## 🔍 Finding Issues to Work On

**On any open-source project:**

1. Go to Issues tab
2. Filter by labels:
   - `good first issue` – beginner-friendly
   - `help wanted` – maintainers need assistance
3. Read through the issue
4. Comment: "I'd like to work on this!"
5. Wait for maintainer to assign you
6. Start coding!

**This is how you contribute to open source!**

---

## ➡️ Next Step

You now know how to organize work with issues! Let's wrap up with team collaboration best practices: [Task 8: Team Workflow](./08-team-workflow.md)

