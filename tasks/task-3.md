# Task 3 — Advanced Git Operations

## 🎯 Goal

Learn how to safely and effectively manage Git history using:

* `git revert`
* `git reset` (soft & hard)
* `git rebase`
* `git cherry-pick`
* `git stash`

---

## 1️⃣ Revert a Commit (Safe for Shared Branches)

### 🧩 Scenario

You accidentally committed the wrong content to `main`, and now you want to undo it safely — without rewriting history.

### 🪜 Steps

1. Make sure you’re on the `main` branch:

   ```bash
   git checkout main
   ```

2. Create a new text file and commit it as a “bad commit”:

   ```bash
   echo "Temporary debug content" > debug.txt
   git add debug.txt
   git commit -m "Added temporary debug content (bad commit)"
   ```

3. Check your recent commits:

   ```bash
   git log --oneline
   ```

   Example output:

   ```
   a1b2c3d Added temporary debug content (bad commit)
   3f8d4b1 Initial project setup
   ```

4. Revert the bad commit using its ID (e.g., `a1b2c3d`):

   ```bash
   git revert a1b2c3d
   ```

5. Git will open your editor to confirm the revert message.
   Save and close to finish.

✅ **Result:**
A new commit is created that undoes the “bad commit.”
Your history remains clean and safe for shared branches.

🧠 **Tip:**
Use `git revert` for public/shared branches (like `main`) to avoid rewriting commit history.

---

## 2️⃣ Soft Reset (Keep Changes Staged)

### 🧩 Scenario

You committed something but forgot to include another file. You want to undo the last commit but keep your changes staged.

### 🪜 Steps

1. Create a simple file and commit it:

   ```bash
   echo "Version 1" > notes.md
   git add notes.md
   git commit -m "Add notes.md"
   ```

2. Realize you forgot to include another change.
   Undo the last commit (but keep changes staged):

   ```bash
   git reset --soft HEAD~1
   ```

3. Now edit your existing file to add missing content:

   ```bash
   echo "Added missing details" >> notes.md
   ```

4. Re-commit your updated work:

   ```bash
   git add notes.md
   git commit -m "Updated notes.md with missing details"
   ```

✅ **Result:**
Your commit is redone with all intended changes.

---

## 3️⃣ Hard Reset (Dangerous; Discards Changes)

### 🧩 Scenario

You made a bad commit and want to completely remove it — including all code changes.

### 🪜 Steps

1. Create another simple file and commit it:

   ```bash
   echo "Wrong content" > wrongfile.txt
   git add wrongfile.txt
   git commit -m "Accidental commit"
   ```

2. Now remove that commit and its changes completely:

   ```bash
   git reset --hard HEAD~1
   ```

✅ **Result:**
The last commit and the file `wrongfile.txt` are permanently gone.
(Use only if you’re sure you don’t need them!)

⚠️ **Warning:**
Avoid using `--hard` on shared branches. It permanently discards data.

---

## 4️⃣ Rebase a Feature Branch onto the Latest Main

### 🧩 Scenario

You’re working on a feature branch, but `main` has new commits. You want to update your branch without merging.

### 🪜 Steps

1. Create and switch to a new feature branch:

   ```bash
   git checkout -b feature/pakeetharan/notes-update
   ```

2. Make a simple change:

   ```bash
   echo "Feature branch update" >> notes.md
   git add notes.md
   git commit -m "Add note from feature branch"
   ```

3. Fetch latest updates from remote:

   ```bash
   git fetch origin
   ```

4. Rebase your branch onto the latest `main`:

   ```bash
   git rebase origin/main
   ```

5. If you face conflicts:

   ```bash
   git status
   # Edit the conflicted files manually
   git add <conflicted-file>
   git rebase --continue
   ```

✅ **Result:**
Your feature branch now includes the latest commits from `main` with a clean, linear history.

🧠 **Tip:**
Rebase is great for your **own** branches — but don’t rebase shared/public ones.

---

## 5️⃣ Cherry-pick a Commit from Another Branch

### 🧩 Scenario

You want to apply a specific commit from another branch (`feature/docs`) to your current branch (`main`).

### 🪜 Steps

1. List commits in the other branch:

   ```bash
   git log feature/docs --oneline
   ```

   Example:

   ```
   7a8b9c1 Add detailed documentation
   5b6a7d2 Fix typos in notes
   ```

2. Switch to your main branch:

   ```bash
   git checkout main
   ```

3. Cherry-pick one commit (e.g., `7a8b9c1`):

   ```bash
   git cherry-pick 7a8b9c1
   ```

✅ **Result:**
That specific commit is now copied onto `main`.

---

## 6️⃣ Stash and Restore Uncommitted Work

### 🧩 Scenario

You started writing notes but need to switch branches to fix a bug quickly.
You don’t want to commit your incomplete work yet.

### 🪜 Steps

1. Make a quick edit:

   ```bash
   echo "Work in progress..." >> notes.md
   ```

2. Stash your uncommitted changes:

   ```bash
   git stash push -m "WIP: updating notes section"
   ```

3. Switch to another branch to fix the issue:

   ```bash
   git checkout main
   # (fix the issue here)
   ```

4. Return to your feature branch:

   ```bash
   git checkout feature/pakeetharan/notes-update
   ```

5. List and restore your stash:

   ```bash
   git stash list
   git stash pop
   ```

✅ **Result:**
Your previous uncommitted work is restored, ready for editing.

---

## 🏁 Success Criteria

You should now be able to:

✅ Revert specific commits safely
✅ Reset (soft/hard) depending on need
✅ Rebase branches cleanly
✅ Cherry-pick commits across branches
✅ Temporarily stash and restore work

---

### 💡 Summary Table

| Action             | Safe for Shared Branch? | Keeps Changes? | Rewrites History? | Example Use                          |
| ------------------ | ----------------------- | -------------- | ----------------- | ------------------------------------ |
| `git revert`       | ✅ Yes                   | ❌ No           | ❌ No              | Undo a bad commit safely             |
| `git reset --soft` | ⚠️ Local only           | ✅ Yes          | ✅ Yes             | Fix last commit but keep changes     |
| `git reset --hard` | ❌ No                    | ❌ No           | ✅ Yes             | Completely undo and discard          |
| `git rebase`       | ⚠️ Local only           | ✅ Yes          | ✅ Yes             | Sync feature branch with latest main |
| `git cherry-pick`  | ✅ Yes                   | ❌ No           | ❌ No              | Copy specific commits                |
| `git stash`        | ✅ Yes                   | ✅ Yes          | ❌ No              | Temporarily store unfinished work    |

---

**End of Task 3 ✅**