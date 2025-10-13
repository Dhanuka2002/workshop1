# Task 2 — Branching, Merging & Collaboration

## Goal

- Learn how to create and switch branches, merge them back into main, and resolve merge conflicts.

---

## What You'll Do

- Create a personal feature branch
- Edit a shared file to simulate a merge conflict
- Resolve the conflict and merge cleanly into the main branch

---

## Steps

### 1. Create and switch to a feature branch:
```
git checkout -b feature/<your-name>/task-2
```

### 2. Update conflict-demo.md
Replace the "name" section in the conflict-demo file with your full name.

   ```
   git add conflict-demo.md
   git commit -m "Add <your-name> contribution to conflict-demo"
   git push -u origin feature/<your-name>/task-2contributions file"
   ```

### 3. Add Pull Requests (PR) to the main
Create pull requests from your branch to the main branch

### 4. Resolve Conflicts
Now you can see there are merge conflicts and can't merge them. These need to be resolved before merging. 

---

Success criteria

- You can create branches, reproduce a merge conflict and resolve it, and merge without losing other changes.
- conflict-demo.md file is available with all the names of your group members

Notes 

- During a real workshop use the GitHub UI to open a Pull Request; reviewers can test and request changes before merging.

- During a real workshop use the GitHub UI to open a Pull Request; reviewers can test and request changes before merging.
