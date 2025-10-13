# Task 1 — Git Basics

Goal
-- Practice the most common local Git commands: init, status, add, commit, log, diff, and restore.

What you'll do

- Initialize a repository
- Create and update a file
- Inspect history and differences
- Undo an uncommitted change

Steps

1. Initialize a new repository (if the repo is already initialized, you can skip this):

   ``` git init ```

2. Create a folder with your name, and inside that, create a file and save your first commit:

   ```
   git add hello.txt
   git commit -m "Add hello.txt"
   ```

3. Modify the file and commit again:

   ```
   git add hello.txt
   git commit -m "Update hello.txt to version 2"
   ```

4. View commit history:
   ```
   git log --oneline
   ```

5. See differences between working tree and last commit:
   ```
   git diff
   ```

6. Finally, Push the changes to the repository
   ```
   git push
   ```   

Success criteria

- You can create commits, view history, inspect diffs, and discard uncommitted changes.

Notes and tips

- Use clear commit messages.
- If you accidentally committed and want to change the commit, we'll cover that in later tasks.
