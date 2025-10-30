# Task 8: Team Workflow & Best Practices

**Goal:** Learn how to collaborate effectively in a team using Git and GitHub.

---

## 👥 How Professional Teams Use Git

**Real teams follow a workflow:**

```
main branch (always stable, always deployable)
    ↓
Feature branches (developers work here)
    ↓
Pull Requests (code review happens here)
    ↓
Merge to main (only after approval)
    ↓
Deploy to production
```

---

## 🌿 Feature Branch Workflow (The Industry Standard)

### The Golden Rules:

1. **`main` is sacred** – always stable, always deployable
2. **Never commit directly to `main`**
3. **Every change gets its own branch**
4. **Every branch gets a PR**
5. **Every PR gets reviewed**
6. **Only merge after approval**
7. **Delete branches after merging**

---

## 📝 Instructions

### Step 1: A Day in the Life

**This is what you do every day as a developer:**

#### Morning Routine
```bash
# Start fresh
git checkout main
git pull origin main

# Check what you're working on today
# (Look at GitHub issues or your project board)
```

#### Start New Work
```bash
# Create a feature branch
git checkout -b feature/add-user-settings

# Work on it
# ... edit files ...
git add .
git commit -m "Add user settings page"

# Push regularly (don't lose work!)
git push -u origin feature/add-user-settings
```

#### Before Submitting PR
```bash
# Make sure you're up to date with main
git checkout main
git pull origin main
git checkout feature/add-user-settings
git merge main

# Fix any conflicts
# Then push
git push
```

#### Submit for Review
```bash
# Go to GitHub
# Open PR
# Request reviews from teammates
# Wait for feedback
```

#### Address Feedback
```bash
# Make requested changes
git add .
git commit -m "Address PR feedback"
git push

# PR updates automatically
```

#### After Merge
```bash
# Switch back to main
git checkout main
git pull origin main

# Delete local branch (it's merged!)
git branch -d feature/add-user-settings
```

---

### Step 2: Branch Naming Conventions

**Use descriptive names with prefixes:**

✅ **GOOD:**
```
feature/user-authentication
feature/dark-mode-toggle
bugfix/login-validation
bugfix/header-alignment
docs/update-readme
docs/api-documentation
hotfix/security-patch
chore/update-dependencies
```

❌ **BAD:**
```
test
fix
final
final2
my-branch
new
```

**Pattern:** `type/short-description`

**Common types:**
- `feature/` – new functionality
- `bugfix/` – fix a bug
- `hotfix/` – urgent production fix
- `docs/` – documentation only
- `chore/` – maintenance tasks
- `refactor/` – code cleanup

---

### Step 3: Commit Message Best Practices

**Use Conventional Commits!**

This is an industry standard that makes commit history scannable and enables automation.

**Format:** `type: description`

**Common types:**
- `feat:` - New feature or addition
- `fix:` - Bug fix
- `docs:` - Documentation only changes
- `style:` - Code style (formatting, semicolons, etc., no logic change)
- `refactor:` - Code refactoring (no feature change or bug fix)
- `test:` - Adding or updating tests
- `chore:` - Maintenance (dependencies, build config, etc.)
- `perf:` - Performance improvement

**Complete Format:**

```
type: short summary (50 chars max)

Optional longer description explaining what and why.
Wrap at 72 characters.

- Bullet points are fine
- Explain the reasoning
- Reference issues

Fixes #42
```

**Rules:**

1. **Always include type prefix:** `feat:`, `fix:`, etc.
2. **Use lowercase after colon:** "feat: add login" not "feat: Add login"
3. **Use imperative mood:** "add feature" not "added feature"
4. **Be specific:** "fix: resolve login timeout" not "fix: fix bug"
5. **No period at the end** of the summary
6. **Blank line** between summary and body

✅ **GOOD EXAMPLES:**

```
feat: add password reset functionality

Implements email-based password reset flow:
- Send reset email with token
- Token expires after 1 hour
- Update password in database

Fixes #127
```

```
fix: resolve navbar alignment on mobile

The navbar was extending beyond screen width on
mobile devices due to fixed width container.

Changed to flex layout with max-width: 100%.

Fixes #203
```

```
docs: update API authentication guide

Added examples for JWT token refresh and error handling.
Clarified rate limiting section.
```

```
chore: upgrade dependencies to latest versions

Updated React 17 → 18, TypeScript 4.9 → 5.0.
Fixed breaking changes in component lifecycle methods.
```

❌ **BAD EXAMPLES:**

```
fixed stuff
```
(No type, vague)

```
update
```
(No type, no context)

```
Add new feature
```
(No type, wrong tense - should be lowercase)

```
feat: Added authentication
```
(Wrong tense - should be "add" not "Added")

```
asdfasdf
```
(Not even trying)

---

### Step 4: Code Review Best Practices

### As the Author (Person Requesting Review):

✅ **DO:**
- Write clear PR description
- Keep PRs small (easier to review)
- Add screenshots for UI changes
- Test your code before requesting review
- Respond to feedback gracefully
- Tag relevant reviewers

❌ **DON'T:**
- Submit huge PRs (1000+ lines)
- Leave confusing code without comments
- Get defensive about feedback
- Force push after people started reviewing

### As the Reviewer:

✅ **DO:**
- Be kind and constructive
- Explain *why* you're suggesting changes
- Praise good code
- Ask questions instead of demanding changes
- Review promptly (don't block teammates)

**Good comments:**
```
"Nice solution! Could we add a comment here explaining the logic?"
"This works, but have you considered using Array.map() instead?"
"Love the clean variable names!"
```

❌ **DON'T:**
- Be mean or dismissive
- Nitpick every tiny detail
- Rewrite someone else's code in comments
- Delay reviews for days

**Bad comments:**
```
"This is wrong."
"Why did you do it this way?"
"I would never write code like this."
```

---

### Step 5: Handling Conflicts

**Scenario: Main changed while you were working**

```bash
# Update main
git checkout main
git pull origin main

# Go back to your branch
git checkout feature/my-feature

# Merge main into your branch
git merge main
```

**If there's a conflict:**
1. Open the conflicted files
2. Look for `<<<<<<<`, `=======`, `>>>>>>>` markers
3. Edit the file to resolve
4. Delete the markers
5. Save the file
6. Stage and commit:
```bash
git add .
git commit -m "Resolve merge conflict with main"
git push
```

---

### Step 6: When Things Go Wrong

### You committed to the wrong branch

```bash
# Undo the commit but keep changes
git reset --soft HEAD~1

# Switch to correct branch
git checkout correct-branch

# Commit again
git add .
git commit -m "Same message"
```

### You accidentally pushed a bad commit

**Best practice:** 
1. **Stop and communicate** - Tell your team immediately
2. **Don't panic** - This happens to everyone
3. **Ask for help** - Your team lead or senior dev can advise

**For beginners:** If you pushed something wrong, it's better to:
- Make a new commit that fixes the issue
- Or ask an experienced teammate for help

**Never** use `git reset --hard` or force push on shared branches!

### You want to change your last commit message

```bash
git commit --amend -m "New message"

# If already pushed (careful!):
git push --force-with-lease
```

**Only do this if no one else has pulled your branch!**

---

## 🎯 Team Collaboration Checklist

Before you start work:
- [ ] Pull latest main
- [ ] Check if anyone else is working on this
- [ ] Create a feature branch with descriptive name

While working:
- [ ] Commit often with clear messages
- [ ] Push regularly to back up work
- [ ] Keep PRs small and focused
- [ ] Test your changes

Before submitting PR:
- [ ] Merge latest main into your branch
- [ ] Fix any conflicts
- [ ] Test again
- [ ] Write clear PR description
- [ ] Reference related issues

During code review:
- [ ] Respond to feedback promptly
- [ ] Ask questions if unclear
- [ ] Make requested changes
- [ ] Thank reviewers

After merge:
- [ ] Pull latest main
- [ ] Delete your feature branch
- [ ] Close related issues (if not auto-closed)

---

## 💡 Key Takeaways

- **Feature branch workflow** is the industry standard
- **`main` is always stable** – treat it with respect
- **Good commit messages** save time later
- **Small PRs** get reviewed faster
- **Kind code reviews** build better teams
- **Communication** prevents conflicts
- **Pull before you push** avoids problems

---

## 🌟 Real-World Team Scenario

**Team: 4 developers working on a web app**

**Alice:**
```bash
git checkout -b feature/user-profile
# Builds user profile page
# Opens PR, reviewed by Bob
# Merges to main
```

**Bob:**
```bash
git checkout -b bugfix/login-error
# Fixes bug, references issue #45
# Opens PR, reviewed by Charlie
# Merges to main
```

**Charlie:**
```bash
git checkout -b feature/dark-mode
# Adds dark mode
# Meanwhile, Alice and Bob's PRs merged
git merge main  # Gets their changes
# Opens PR, reviewed by Dana
# Merges to main
```

**Dana:**
```bash
git checkout -b docs/update-api-guide
# Updates documentation
# Opens PR, quick review
# Merges to main
```

**Result:** 4 developers working in parallel, no conflicts, main stays stable!

---

## 🛡️ Protecting Main Branch

**Many teams enable "Branch Protection" on GitHub:**

**Settings → Branches → Add rule for `main`:**
- ✅ Require pull request before merging
- ✅ Require approvals (1-2 reviewers)
- ✅ Require status checks to pass (tests, linting)
- ✅ Prevent force push
- ✅ Prevent deletion

**This means:**
- You **can't** push directly to main
- You **must** use PRs
- Code **must** be reviewed
- Tests **must** pass

**This keeps main stable and prevents mistakes!**

---

## 🎉 Congratulations!

You've completed all the Git workshop tasks! You now know:

- ✅ Git setup and configuration
- ✅ The three areas (workspace, staging, repository)
- ✅ Creating commits with good messages
- ✅ Working with feature branches
- ✅ Pushing and pulling
- ✅ Handling merge conflicts
- ✅ Creating and reviewing pull requests
- ✅ Using GitHub issues to track work
- ✅ Team collaboration best practices

---

## 📚 Keep Learning

### Next Steps:

1. **Use Git for every project** – even small ones
2. **Contribute to open source:**
   - Find a project on GitHub
   - Look for `good first issue` labels
   - Fork it, make changes, submit PR!
3. **Explore advanced topics:**
   - `git stash` – temporary save work
   - `git cherry-pick` – copy specific commits
   - `git reflog` – time machine for Git
   - `git bisect` – find which commit broke something
4. **Build your GitHub profile:**
   - Green squares show your activity
   - Pin your best projects
   - Write good READMEs

### Resources:

- [GitHub Skills](https://skills.github.com/) – Interactive tutorials
- [Git Documentation](https://git-scm.com/doc) – Official docs
- [Oh Shit, Git!?!](https://ohshitgit.com/) – Fixing mistakes
- UAIS Discord – Ask questions!

---

## 🚀 You're Ready!

Go build cool projects, collaborate with teams, and contribute to open source.

Git is a skill that will serve you throughout your entire career.

**Happy coding!** 🎉

