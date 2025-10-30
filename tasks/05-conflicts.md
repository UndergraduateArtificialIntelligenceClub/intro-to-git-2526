# Task 5: Handling Merge Conflicts

**Goal:** Face a merge conflict and live to tell the tale.

---

## ⚔️ What's a Merge Conflict?

A conflict happens when:
1. You edit line 5 of a file
2. Someone else edits line 5 of the **same file**
3. You both try to merge

Git says: **"I don't know which version to keep. You decide."**

---

## 🎨 How Git Shows Conflicts

When there's a conflict, Git marks the file like this:

```diff
<<<<<<< HEAD
UAIS rocks at AI events!
=======
UAIS runs awesome AI workshops!
>>>>>>> feature-yourname
```

- `<<<<<<< HEAD` = your current branch's version
- `=======` = separator
- `>>>>>>> feature-yourname` = the incoming version

---

## 📝 Instructions

### Step 1: Create a Conflict (On Purpose!)

**Everyone do this:**

1. Open `practice/conflict-demo.txt`
2. Find line 3 (it should say something like "Edit this line!")
3. **Change it to something unique** (e.g., "Git is amazing!")
4. Save the file

---

### Step 2: Commit Your Change

```bash
git add practice/conflict-demo.txt
git commit -m "feat: update conflict demo line"
```

---

### Step 3: Try to Merge

**Switch to main:**
```bash
git checkout main
```

**Try to merge your branch:**
```bash
git merge feature-yourname
```

**What happens:**
- **If you're the first person:** Merge succeeds! ✅
- **If someone else merged first:** **CONFLICT!** 💥

---

### Step 4: Resolve the Conflict

**If you got a conflict, Git will say:**
```
CONFLICT (content): Merge conflict in practice/conflict-demo.txt
Automatic merge failed; fix conflicts and then commit the result.
```

**Open `practice/conflict-demo.txt` in VS Code.**

You'll see:
```diff
<<<<<<< HEAD
UAIS rocks at AI events!
=======
Git is amazing!
>>>>>>> feature-yourname
```

---

### Step 5: Pick a Version

**You have 3 options:**

1. **Keep your version** (delete the other lines and the markers)
2. **Keep their version** (delete your lines and the markers)
3. **Combine both** (write a new line that includes both ideas)

**Example resolution:**
```
UAIS rocks at AI events and runs awesome workshops!
```

**Delete all the markers (`<<<<<<<`, `=======`, `>>>>>>>`)**

---

### Step 6: Mark as Resolved

**Stage the fixed file:**
```bash
git add practice/conflict-demo.txt
```

**Commit the merge:**
```bash
git commit -m "fix: resolve conflict in conflict-demo.txt"
```

**Note:** Use `fix:` for conflict resolutions since you're fixing a merge issue.

**Done!** Conflict resolved.

---

## 🎯 Success Criteria

- [ ] Created a conflict by editing the same line as someone else
- [ ] Saw the conflict markers in the file
- [ ] Resolved the conflict by editing the file
- [ ] Staged and committed the resolution

---

## 💡 Key Takeaways

- Conflicts are normal! Don't panic.
- Git shows you **exactly** where the conflict is
- **You** decide which version to keep
- Always stage (`git add`) after fixing
- Read the error messages — Git tells you what to do

---

## 🆘 Troubleshooting

**Stuck in a merge?**
```bash
git merge --abort
```
This cancels the merge and goes back to before.

**Made a mistake resolving?**
```bash
git reset --merge
```
Resets the merge state.

---

## ➡️ Next Step

Conflicts conquered! Now learn how to save work without committing: [Task 6: Stashing](./06-stash.md)

