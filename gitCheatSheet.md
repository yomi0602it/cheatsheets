## Git Command Cheat Sheet

| Command | Explanation | Example |
| :--- | :--- | :--- |
| `git clone` | Clone a remote repository given the URL | `git clone https://github.com/Pierian-Data/Git-and-GitHub-Zero-to-Hero.git` |
| `git add` | Stage files / add files to the index for subsequent committing | `git add ReadMe.md` |
| `git status` | Lists all added, changed and newly created files. | `git status` |
| `git reset` | Undo changes / unstage files / go back to commit | `git reset`<br>`git reset test.txt`<br>`git reset --hard 5b331f3` |
| `git restore` | Unstage specific files / undo specific changes | `git restore test.txt`<br>`git restore --staged test.txt` |
| `git log` | Show commit history | `git log --after="2022-1-1"`<br>`git log --after="yesterday"`<br>`git log -n 10`<br>`git log --author="Jose"` |
| `git diff` | Visualize changes | `git diff --cached test.txt`<br>`git diff 4598 3g62 test.txt`<br>`git diff main development` |
| `git commit` | Commit changes after staging them | `git commit -m "Updated ReadMe.md"`<br>`git commit --amend -m "your new message"` |
| `git push` | Push new commits to the remote repository | `git push`<br>`git push origin`<br>`git push origin main`<br>`git push origin main:test` |
| `git branch` | List, create, or delete branches | `git branch`<br>`git branch development`<br>`git branch --delete development` |
| `git switch` | Switch to another branch | `git switch development`<br>`git switch -c development2`<br>`git switch -d h98uab`<br>`git switch -m main` |
| `git checkout` | Switch branches or restore working tree files | `git checkout development`<br>`git checkout -b development2`<br>`git checkout h98uab`<br>`git checkout -m main`<br>`git checkout test.txt` |
| `git merge` | Merge / join two branches | `git merge devel`<br>`git merge devel1 devel2`<br>`git merge -s ours devel` |
| `git tag` | Create, list, delete or verify a tag | `git tag v1.0`<br>`git tag v1.0 -a`<br>`git tag --delete v1.0` |
| `git fetch` | Fetch changes from the remote repository (does not update head) | `git fetch`<br>`git fetch origin`<br>`git fetch origin main`<br>`git fetch origin main:test` |
| `git pull` | Update local version with remote version. (git fetch + git merge) | `git pull`<br>`git pull origin`<br>`git pull origin main`<br>`git pull origin main:test` |
| `git rebase` | Rewrite commit history | `git rebase -i HEAD~5` |
| `git revert` | Revert existing commits and create new commit with these changes | `git revert 2fc0df` |
| `git stash` | Stash changes for later use | `git stash`<br>`git stash list`<br>`git stash show`<br>`git stash pop`<br>`git stash pop stash@{2}` |
| `git clean` | Delete all files not tracked by git | `git clean`<br>`git clean -n`<br>`git clean -x` |
