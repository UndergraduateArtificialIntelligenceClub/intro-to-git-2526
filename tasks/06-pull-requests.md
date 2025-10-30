# Task 6: Pull Requests & Code Review

**Goal:** Learn how teams review and merge code using Pull Requests.

---

## 🔍 What's a Pull Request?

A **Pull Request (PR)** is a request to merge your branch into main. It's where:
- Teammates review your code
- You discuss changes
- Code gets approved before merging

**Think of it as:** "Hey team, can you check this out before we add it to main?"

---

## 🎨 The PR Workflow

```
1. Write code on your branch
2. Push to GitHub
3. Open a Pull Request
4. Team reviews and comments
5. You address feedback
6. PR gets approved
7. Merge into main
8. Delete the branch
```

---

## 📝 Instructions

### Step 1: Make Sure Your Branch is Pushed

```bash
git checkout feature/add-yourname
git push -u origin feature/add-yourname
```

If you already pushed, you'll see "Everything up-to-date".

---

### Step 2: Go to GitHub

Open the repository in your browser:
```
https://github.com/UAIS/intro-to-git-2526
```

**You should see a yellow banner:**
```
feature/add-yourname had recent pushes
[Compare & pull request]
```

**Click "Compare & pull request"**

---

### Step 3: Fill Out Your PR

**Title:**  
Short, clear summary with conventional commit prefix (50 chars or less)
```
feat: add [Your Name] to participants list
```

**Description:**  
Explain what you changed and why. Use markdown!

```markdown
## What I Changed
- Added my name to `practice/participants.txt`

## Why
- Part of the UAIS Git workshop exercise

## Testing
- Verified my name appears in the file
- No other changes made
```

**Then click "Create pull request"**

---

### Step 4: Understand the PR Interface

**Tabs you'll see:**

1. **Conversation** – Comments and discussion
2. **Commits** – List of all commits in this PR
3. **Files changed** – Diff view showing what changed

**Click "Files changed"** to see your changes highlighted.

---

### Step 5: Review Someone Else's PR

**Find a teammate's PR:**
1. Go to the **"Pull requests"** tab
2. Click on someone else's open PR
3. Click **"Files changed"**

**Leave a helpful comment:**
- Click the `+` button next to a line of code
- Write a constructive comment:
  - ✅ "Nice work! Welcome to the workshop!"
  - ✅ "Minor: there's an extra space here"
  - ❌ "This is wrong"

**Submit your review:**
1. Click **"Review changes"**
2. Leave a comment (optional)
3. Choose **"Approve"**
4. Click **"Submit review"**

---

### Step 6: Respond to Feedback

**If someone left comments on your PR:**

1. Read the feedback
2. If they requested changes:
   ```bash
   git checkout feature/add-yourname
   # Make the change
   git add .
   git commit -m "Address PR feedback"
   git push
   ```
3. The PR updates automatically!
4. Reply to their comment: "Fixed! Thanks for catching that."

---

### Step 7: Merge Your PR

**Once approved:**

1. Go back to your PR
2. Click **"Merge pull request"**
3. Choose **"Create a merge commit"** (the default)
4. Click **"Confirm merge"**

**Congratulations!** Your code is now in `main`! 🎉

---

### Step 8: Delete Your Branch

**After merging, GitHub will ask:**
```
Delete branch [Delete branch]
```

**Click it!** This keeps the repo clean. Don't worry — the commits are still in `main`.

---

### Step 9: Update Your Local Main

```bash
git checkout main
git pull origin main
```

**You should see your changes now in main!**

---

## 🎯 Success Criteria

- [ ] Created a Pull Request with title and description
- [ ] Reviewed at least one other person's PR
- [ ] Received approval on your PR
- [ ] Merged your PR into main
- [ ] Deleted your feature branch
- [ ] Pulled the latest main to your computer

---

## 💡 Key Takeaways

- **PRs enable code review** before merging
- **Good descriptions help reviewers** understand your changes
- **Be kind and constructive** when reviewing
- **Merge commits preserve history** of who did what
- **Delete branches after merging** keeps things tidy
- **This is how professional teams work**

---

## 🌟 Real-World PR Example

**Title:**
```
feat: add dark mode toggle to settings page
```

**Description:**
```markdown
## Summary
Implements user-requested dark mode feature.

## Changes
- Add toggle button to settings page
- Implement dark theme CSS
- Save preference to localStorage
- Apply theme on page load

## Testing
- Tested on Chrome, Firefox, Safari
- Toggle persists across sessions
- Meets WCAG AA contrast standards

Fixes #127
```

**Notice:**
- Clear summary
- Detailed changes
- Testing notes
- References the issue number

---

## 🔗 Linking PRs to Issues

**In your PR description, you can write:**
- `Fixes #42` – closes issue #42 when PR merges
- `Closes #42` – same thing
- `Resolves #42` – same thing
- `Related to #42` – mentions but doesn't close

**This auto-closes issues when PRs merge!**

---

## 🚨 Draft PRs

**Want feedback before you're done?**

Create a **Draft PR:**
1. Click the dropdown next to "Create pull request"
2. Select "Create draft pull request"

**Use this when:**
- You want early feedback
- Work is in progress
- You need help/discussion

**Mark as ready when done:**
Click "Ready for review" button.

---

## ➡️ Next Step

You've mastered PRs! Now let's learn how teams organize work: [Task 7: GitHub Issues](./07-github-issues.md)

