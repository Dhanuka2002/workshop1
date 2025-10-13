# Contributing & Workshop workflow

Follow this guide during the workshop to keep contributions consistent and reviewable.

Branch naming

- feature/<your-name>/task-<n>

Commit messages

- Use imperative, concise messages: "Add X", "Fix Y", "Update Z"

Pull Request checklist (use when opening PR)

- [ ] I created a branch for this task
- [ ] My commit messages are clear
- [ ] My changes build (if applicable)
- [ ] I ran the workshop steps from the task file

Resolving conflicts

- If you encounter a merge conflict, open the conflicting file, read the markers (<<<<<<<, =======, >>>>>>>), resolve manually, then add and commit the resolved file.

Review process

- Assign one reviewer.
- Reviewer should check correctness, clarity, and whether the merge introduces conflicts.

Good to know

- For shared branches (like `main`), prefer `git revert` over `git reset`.
- Use `git stash` to temporarily save WIP changes when switching contexts.
