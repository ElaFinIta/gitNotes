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

## squash commits
Combines commits, rewrites history. Before pushing and merging into main, to clean up all the commits into one commit about a feature

```sh
git rebase -i HEAD~3
```

where `-i` stands for interactive and `HEAD~3` means starting from HEAD for 3 commits.
To enter the interactive edit press:

- `i` and replace `pick` in front of the commits you want to squash with `squash` (`fixup` will do the same but discard the commit message associated with the commit). Leave the first `pick`.


We are saying that we want to meld the second and third commit into the first one.
Save and exit interactive mode with:

- esc
- :wq
- enter

Now you can refactor the commit message:

- `i` and hash `#`in front of messages you want to omit. Leave one message and possibly modify it.

Save and exit interactive mode with:

- esc
- :wq
- enter

Now you can push the squashed commits.

Remember that squashing will change the git history. So if you have already pushed the branch to remote then it is not advisable to squash.
Always squash before you push the changes to remote.
If we've squashed already pushed commits, and we would like to publish the squashed result, we have to do a force push (git push -f).

## Using squash when merging the branch

When we are ready to merge changes of a feature branch into the main branch:

```sh
git merge --squash target_branch_name
```

This command will take all the commits from the target branch, squash them, and stage all changes in the current branch. Then you can commit all the changes in a single commit.


**or just use GitHub SQUASH AND MERGE button when merging a branch into main.**

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


### Delete a local branch 
```sh
git branch -d <local-branch>
```

or if the branch is not fully merged:
```sh
git branch -D <local-branch>
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

## To change the URL for a remote Git repository (ex. cloned repo):
```shell
git remote set-url origin new_git_url_here
```

### About ignoring files in `.gitignore`:
https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files

## Sources:
- https://www.atlassian.com/git/tutorials/setting-up-a-repository
- git stash: https://www.atlassian.com/git/tutorials/saving-changes/git-stash
