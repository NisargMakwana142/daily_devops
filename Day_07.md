## Day 7 - Git & GitHub Basics

### Git vs GitHub
- Git - global information tracker (local version control)
- GitHub - web-based platform that hosts Git repositories in the cloud

### File states
Untracked → Staged → Tracked

```bash
git init                    # initialize empty repo, new files start untracked
git add file_name           # untracked -> staged
git rm --cached file_name   # staged -> untracked (keeps file on disk)
git commit -m "message"     # staged -> tracked
git restore file_name       # restores a deleted/modified file
```

### Branching
A branch = separate workspace / pointer to a line of commits

```bash
git branch              # list all branches
git checkout -b name    # create + switch to new branch
git checkout name       # switch branch
git switch name         # switch branch (alt)
git merge name          # merge given branch into current branch
```

### Remote (GitHub)

```bash
git remote add origin url                                # connect to remote repo
git remote -v                                            # show remote URL
git remote set-url origin https://token@github.com/url   # auth via token
git push origin main                                     # push local commits
git pull origin main                                     # pull remote changes
git clone url                                            # copy full remote repo
```

### Other essentials
- `git diff` - shows differences between changes
- `.gitignore` - file listing what Git should ignore
- **fork** - your own copy of someone else's repo on GitHub

### Next up
Continuing Git and GitHub.
