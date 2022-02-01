# Git commands

## git stash
I used this to pull from main after I made some local changes on my branch (otherwise conflicts).
```shell
git stash
```
The git stash command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy. It's local to your Git repository; stashes are not transferred to the server when you push.
After git stash you can have a clean working tree. You can do other Git operation like pull.

You can reapply previously stashed changes with:
```shell
git stash pop
```

Git stash will not stash new files in your working copy that have not yet been staged.
To stash also your untracked files:
```shell
git stash -u
```
To see the stash list:
```
git stash list
```
will show:
```shell
stash@{0}: WIP on main: 5002d47 our new homepage
stash@{1}: WIP on main: 5002d47 our new homepage
stash@{2}: WIP on main: 5002d47 our new homepage
```
where WIP stands for work in progress. To add a message:
```shell
git stash save "message here"
```

Apply a specific stash number 2 (default is 0):
```shell
git stash pop stash@{2}
```

Delete a specific stash (number 1):
```shell
git stash drop stash@{1}
```

Delete all stash:
```shell
git stash clear
```

## git pull


```shell
git pull 
```
is equivalent to:
git fetch origin HEAD **and** git merge HEAD
where HEAD is ref pointing to the current branch.

git pull will NOT remove your local untracked files

## git add
Add a single file:
```shell
git add file_name
```

Interactive staging session that lets you choose portions of a file to add to the next commit.:
```shell
git add -p
```

List of commits:
```shell
git log
```

## git rebase
Rebase the current branch onto <base>. <base> can be a commit ID,
branch name...
```shell
git rebase <base>
```

## branches (only commits/pushes to default branch are counted as contributions)
See what branch you are in:
```shell
git branch
```

See remote branches:
```shell
git branch -r
```

See all remote and local branches:
```shell
git branch -a
```

Create a new branch:
```shell
git checkout -b my-branch-name
```

Switch to a Branch In Your Local Repo
```shell
git checkout my-branch-name
```

### Rename a local branch:
```shell
git branch -m old-name new-name
```

### Rename a remote branch:
1.  overwrite the remote branch
```shell
git push origin :old-name new-name
```

### Delete the branch with the old name on the remote repository
```sh
git push origin --delete old-name
```

## git push
Upload the local state of ＜branch-name＞ to the remote repository specified by ＜remote-name＞.
```shell
git push <remote-name> <branch-name>
```
Example:
```shell
git push origin dev
```
will upload the locale state of branch dev to the remote (origin).
```shell
git checkout my-branch-name
```

## remove git tracking from a folder
from inside the folder: BE CAREFUL! This command will recursively remove all files from the specified folder!
```shell
rm -rf .git // Remove git tracking
```

## insert commit message in editor:
- press "i" (i for insert)
- write your merge message
- press "esc" (escape)
- write ":wq" (write & quit)
- then press enter

### About ignoring files in `.gitignore`:
https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files

## Sources:
- https://www.atlassian.com/git/tutorials/setting-up-a-repository
- git stash: https://www.atlassian.com/git/tutorials/saving-changes/git-stash
