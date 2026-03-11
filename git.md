# Git Cheatsheet

## Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor vim
git config --list                          # Show all config settings
```

## Create & Clone

```bash
git init                                   # Initialize a local repository
git init <directory>                       # Initialize in a specific directory
git clone <url>                            # Clone a remote repository
git clone <url> <directory>               # Clone into a specific directory
```

## Staging & Snapshots

```bash
git status                                 # Show working tree status
git add <file>                             # Stage a specific file
git add .                                  # Stage all changes
git add -p                                 # Interactively stage hunks
git commit -m "message"                    # Commit staged changes
git commit -am "message"                   # Stage tracked files and commit
git commit --amend                         # Amend the last commit
git reset HEAD <file>                      # Unstage a file
git checkout -- <file>                     # Discard changes in working directory
```

## Branching & Merging

```bash
git branch                                 # List local branches
git branch -a                              # List all branches (local + remote)
git branch <name>                          # Create a new branch
git branch -d <name>                       # Delete a branch
git branch -D <name>                       # Force-delete a branch
git checkout <branch>                      # Switch to a branch
git checkout -b <branch>                   # Create and switch to a new branch
git switch <branch>                        # Switch to a branch (modern)
git switch -c <branch>                     # Create and switch (modern)
git merge <branch>                         # Merge branch into current branch
git merge --no-ff <branch>                 # Merge with a merge commit
git rebase <branch>                        # Rebase current branch onto branch
git rebase -i HEAD~<n>                     # Interactive rebase for last n commits
```

## Remote Repositories

```bash
git remote -v                              # List remotes
git remote add origin <url>               # Add a remote
git remote remove <name>                   # Remove a remote
git fetch                                  # Fetch all remotes
git fetch <remote>                         # Fetch a specific remote
git pull                                   # Fetch and merge
git pull --rebase                          # Fetch and rebase
git push                                   # Push to default remote/branch
git push -u origin <branch>               # Push and set upstream
git push --force-with-lease               # Safe force push
git push origin --delete <branch>         # Delete remote branch
```

## Inspection & Comparison

```bash
git log                                    # Show commit history
git log --oneline --graph --all           # Compact graph view
git log -p                                 # Show patches
git log --author="name"                   # Filter by author
git diff                                   # Show unstaged changes
git diff --staged                          # Show staged changes
git diff <branch1>..<branch2>             # Diff between two branches
git show <commit>                          # Show a commit
git blame <file>                           # Show who changed each line
```

## Stashing

```bash
git stash                                  # Stash working changes
git stash push -m "message"               # Stash with a description
git stash list                             # List stashes
git stash pop                              # Apply and remove latest stash
git stash apply stash@{n}                 # Apply a specific stash
git stash drop stash@{n}                  # Delete a specific stash
git stash clear                            # Delete all stashes
```

## Tags

```bash
git tag                                    # List tags
git tag <name>                             # Create a lightweight tag
git tag -a <name> -m "message"            # Create an annotated tag
git push origin <tag>                     # Push a tag
git push origin --tags                    # Push all tags
git tag -d <name>                          # Delete a local tag
git push origin --delete <tag>            # Delete a remote tag
```

## Undoing Changes

```bash
git revert <commit>                        # Create a revert commit
git reset --soft HEAD~1                   # Undo last commit, keep changes staged
git reset --mixed HEAD~1                  # Undo last commit, keep changes unstaged
git reset --hard HEAD~1                   # Undo last commit, discard changes
git clean -fd                              # Remove untracked files and directories
git restore <file>                         # Restore a file (modern)
git restore --staged <file>               # Unstage a file (modern)
```

## Useful Shortcuts

```bash
git shortlog -sn                           # Contributor summary
git log --since="2 weeks ago"             # Commits in the last 2 weeks
git bisect start                           # Start binary search for a bug
git cherry-pick <commit>                   # Apply a commit to current branch
git reflog                                 # Show history of HEAD movements
```
