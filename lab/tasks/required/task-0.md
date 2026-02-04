# Practice the git workflow

**Time:** ~15 min

**Purpose:** Practice our git workflow on a simple task before starting the main assignments.

**Context:** This task is an opportunity to practice the full cycle (Issue → Branch → Commits → PR → Review → Merge) on something simple. If anything goes wrong here, it's easy to fix.

## Steps

### 1. Create an issue

Title: `[Task] Add my name to contributors`

### 2. Create a branch

On the issue page, click `Create a branch` in the right sidebar.

Or use the terminal:

```bash
git checkout -b add-contributor-<your-name>
```

### 3. Add your name

1. Open `CONTRIBUTORS.md`.
2. Add your name below the comment:

    ```markdown
    - Your Name (@your-github-username)
    ```

3. Save the file.

### 4. Commit and push

```bash
git add CONTRIBUTORS.md
git commit -m "docs: add my name to contributors"
git push -u origin <branch-name>
```

### 5. Create a Pull Request

1. Go to your repo on GitHub.
2. Click `Compare & pull request`.
3. Title: `Add [Your Name] to contributors`
4. Description: `Closes #<issue-number>`
5. Click `Create pull request`.

### 6. Get review and merge

1. Request a review from your partner.
2. Once approved, click `Merge pull request`.
3. Delete the branch when prompted.

## Acceptance criteria

- [ ] Issue created
- [ ] Branch created from the issue
- [ ] Name added to `CONTRIBUTORS.md`
- [ ] Commit message follows `type: description` format
- [ ] PR created and linked to issue
- [ ] Partner reviewed and approved
- [ ] PR merged
