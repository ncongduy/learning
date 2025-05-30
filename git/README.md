## How to tag version via git

- tag version for specific commit: git tag -a 1.0.0 <commit-hash> -m "Release version 1.0.0"
- push all tags to origin: git push origin --tags
- view tag: git tag
- show specific tag: git show 1.0.0
- delete locally: git tag -d <tag-name>
- delete remote repo: git push origin --delete tag <tag-name>

## Basic Commands

| Command                   | Description                          |
| ------------------------- | ------------------------------------ |
| `git init`                | Initialize a new Git repo            |
| `git clone <url>`         | Clone a repo                         |
| `git status`              | Show status of working directory     |
| `git add <file>`          | Stage file(s) for commit             |
| `git commit -m "message"` | Commit staged changes                |
| `git push`                | Push changes to remote repo          |
| `git pull`                | Fetch and merge changes from remote  |
| `git fetch`               | Fetch changes from remote (no merge) |

## Branching and Merging

| Command                    | Description                             |
| -------------------------- | --------------------------------------- |
| `git branch`               | List local branches                     |
| `git branch <name>`        | Create a new branch                     |
| `git checkout <name>`      | Switch to a branch                      |
| `git switch <name>`        | Newer alternative to `checkout`         |
| `git merge <branch>`       | Merge another branch into current one   |
| `git rebase <branch>`      | Rebase current branch onto another      |
| `git cherry-pick <commit>` | Apply specific commit to current branch |

## Clean-Up and Undo

| Command                     | Description                             |
| --------------------------- | --------------------------------------- |
| `git reset --hard <commit>` | Reset to commit and discard all changes |
| `git reset --soft <commit>` | Reset to commit but keep changes staged |
| `git checkout -- <file>`    | Revert file to last committed state     |
| `git clean -fd`             | Delete untracked files and dirs         |
| `git reflog`                | View HEAD history, even deleted commits |

## Searching and Inspecting

| Command                     | Description                 |
| --------------------------- | --------------------------- |
| `git log`                   | View commit history         |
| `git log --oneline --graph` | Visualize branches          |
| `git diff`                  | Show unstaged changes       |
| `git diff --cached`         | Show staged changes         |
| `git blame <file>`          | See line-by-line authorship |
| `git grep "pattern"`        | Search tracked files        |
| `git show <commit>`         | Show commit details         |

## Stashing and Patching

| Command             | Description                  |
| ------------------- | ---------------------------- |
| `git stash`         | Save uncommitted changes     |
| `git stash apply`   | Reapply the latest stash     |
| `git stash pop`     | Reapply and delete the stash |
| `git stash list`    | View stashes                 |
| `git apply <patch>` | Apply a patch                |

## Remote Commands

| Command                       | Description                  |
| ----------------------------- | ---------------------------- |
| `git remote -v`               | Show remotes                 |
| `git remote add origin <url>` | Add remote origin            |
| `git push -u origin <branch>` | Push and set upstream branch |
| `git remote remove origin`    | Remove a remote              |

## Advanced Tools

| Command         | Description                         |
| --------------- | ----------------------------------- |
| `git bisect`    | Find buggy commit via binary search |
| `git submodule` | Work with submodules                |
| `git archive`   | Create zip/tar archive of repo      |