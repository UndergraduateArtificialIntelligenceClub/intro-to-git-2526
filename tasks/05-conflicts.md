# Task 5: Understanding Merge Conflicts

**Goal:** Learn how merge conflicts work by watching the instructors demonstrate them live.

**Note:** This is a **demo-only task**. You'll watch the instructors create and resolve a conflict. Understanding conflicts is important, but we won't have everyone create them (that would get chaotic!).

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
UAIS rocks at AI events!
UAIS runs awesome AI workshops!
```

- `<<<<<<< HEAD` = your current branch's version
- `=======` = separator
- `>>>>>>> feature-yourname` = the incoming version

---

## 📺 What You'll See (Demo for the sake of time)

### The Setup
We'll demi this! 

**Hamidat:**
1. Creates a branch
2. Edits line 5 in `practice/demo-conflict.md`
3. Commits and pushes
4. Opens a PR and merges it ✅

**Aarush:**
1. Also creates a branch (from the same starting point)
2. Edits the **same line 5** differently
3. Commits and pushes
4. Tries to merge → **CONFLICT!** 💥

**Watch what happens!**

---

## 🔍 What the Conflict Looks Like

**When Instructor 2 tries to merge, Git will say:**
```
CONFLICT (content): Merge conflict in practice/demo-conflict.md
Automatic merge failed; fix conflicts and then commit the result.
```

```diff
<<<<<<< HEAD
Learning Git with UAIS is awesome!
=======
Git is an essential tool for modern development!
>>>>>>> main
```

**The conflict markers explained:**
- `<<<<<<< HEAD` = Instructor 2's version (current branch)
- `=======` = separator
- `>>>>>>> main` = Instructor 1's version (already in main)

---

## 🛠️ How to Resolve Conflicts

### Option 1: Keep One Version
Delete the other version and all the markers.

### Option 2: Keep Both
Combine ideas from both versions.

### Option 3: Write Something New
Create a brand new line that's better than both.

```
Learning Git with UAIS is awesome! Git is an essential tool for modern development!
```

**Delete all the markers** (`<<<<<<<`, `=======`, `>>>>>>>`)

---

## ✅ Finishing the Resolution

**Watch as the instructor:**

1. **Saves the file** (conflict is resolved)

2. **Stages it:**
```bash
git add practice/demo-conflict.md
```

3. **Commits the merge:**
```bash
git commit -m "fix: resolve conflict in demo file"
```

4. **Pushes:**
```bash
git push
```

5. **The PR now shows:** ✅ No conflicts, ready to merge!

**That's it!** Conflict resolved and both instructors' ideas are in the code.

---

## 🎯 What You Should Understand

After watching the demo, you should understand:

- [ ] What causes a merge conflict (two people editing the same line)
- [ ] What the conflict markers mean (`<<<<<<<`, `=======`, `>>>>>>>`)
- [ ] That conflicts require a human decision (Git can't guess)
- [ ] The steps to resolve: edit file → stage → commit
- [ ] That conflicts are normal and fixable

---

## 💡 Key Takeaways

- **Conflicts are normal** – They happen on every team
- **Don't panic** – Git shows you exactly what and where
- **Communication helps** – Talk to the person you conflicted with
- **You decide** – Git can't guess which version is right
- **Read the markers** – They tell you what each version is
- **Always test after** – Make sure your resolution works

---

## 🙋 When You'll Actually Do This

In real development:
- You'll pull `main` and get a conflict
- You'll open the file, see the markers
- You'll decide what to keep (often by talking to your teammate)
- You'll test that your resolution works
- You'll commit and push

**For now:** Just understanding how they work is enough. You'll handle conflicts naturally when collaborating on real projects!

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

Conflicts conquered! Now let's learn how teams review code: [Task 6: Pull Requests](./06-pull-requests.md)

