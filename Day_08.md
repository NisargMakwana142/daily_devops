## Day 8 - Pull Requests, Revert, Reset, Stash, Cherry-pick

Short day today.

### Pull Request (PR)
A proposal to merge changes from one branch into another in a Git repository. Practiced raising a PR on GitHub.

### git revert
```bash
git revert log_id
```
Undoes a specific commit by creating a new commit that reverses it (history preserved).

If conflicts occur:
```bash
git revert --continue
```

### git reset (use with caution)
```bash
git reset log_id --soft
```
Three flags:
- `--soft` → untracked + staged
- `--mixed` → untracked
- `--hard` → deleted entirely

Rewrites history - risky, especially on shared branches.

### Stashing
```bash
git stash           # save working directory (including untracked)
git stash pop       # restore most recent stash, remove from list
git stash list      # show all saved stashes
git stash pop 1     # restore stash at index 1
```

### Cherry-picking
```bash
git cherry-pick log_id
```
Applies one specific commit from another branch, without merging the whole branch.

### Next up
A little more Git/GitHub left.
