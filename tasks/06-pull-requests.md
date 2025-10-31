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

## 🏢 Why This Workflow Exists

**Why can't we just push directly to `main`?**

In professional teams:
- **`main` is protected** – You physically can't push to it
- **Code review is required** – At least one person must approve your PR
- **Tests must pass** – Automated checks run before merge
- **Main stays stable** – Production code is always deployable

**The typical workflow:**
1. You fork or clone a repo
2. Create a feature branch for your change
3. Make your changes and commit
4. Push your branch to GitHub
5. Open a PR to propose merging into main
6. Maintainers/teammates review your code
7. You address feedback if needed
8. Once approved, someone merges it (you or a maintainer)
9. Your feature branch gets deleted

**Each repo usually has a `CONTRIBUTING.md`** file that explains their specific process, but this is the general pattern everywhere.

**This prevents:**
- Breaking production code
- Merging buggy changes
- Code that hasn't been reviewed
- Losing track of what changed

**This enables:**
- Quality control through review
- Knowledge sharing (others see your code)
- Discussion and collaboration
- Safe experimentation

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

### Alternative: Create PR from Command Line

**If you have GitHub CLI installed, you can skip the browser!**

```bash
gh pr create --title "feat: add my name to participants list" --body "Added my name to participants.txt as part of workshop"
```

This opens the PR directly from your terminal! Way faster once you get comfortable with it.

**View your PR:**
```bash
gh pr view --web
```

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
2. Write an overall comment (optional but recommended)
3. **Choose one of three options:**

   **Comment** 💬
   - Just leaving feedback, no formal approval
   - Use this when you have questions or suggestions
   - Doesn't block merging

   **Approve** ✅
   - You've reviewed and it looks good
   - You're saying "this is ready to merge"
   - Often required before merging (depends on repo settings)

   **Request changes** 🔴
   - Issues need to be fixed before merging
   - Use this when something's broken or needs improvement
   - Blocks merging until you approve later

4. Click **"Submit review"**

**For this workshop:** Use **"Approve"** to help your teammates merge!

**Pro tip:** Good reviewers:
- Point out both good things and issues
- Explain *why* something should change
- Are kind and constructive
- Ask questions instead of demanding changes

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

### Step 9: Clean Up Locally

**Switch back to main and pull the merged changes:**

```bash
git checkout main
git pull origin main
```

**You should see your changes now in main!**

**Delete your local branch** (it's merged and no longer needed):

```bash
git branch -d feature/add-yourname
```

**Why delete branches?**
- Keeps your local repo clean
- Prevents confusion about which branches are active
- `main` now has all your changes anyway

**Pro tip:** Use `git branch` to see all your branches. Delete merged ones regularly!

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

