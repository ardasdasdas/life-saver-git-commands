# Life and Time Saver Git Commands 🚀
A repository that contains life and timer saver git commands; rollback, revert, etc. (in-progress)

- [How to delete all local git branches?](#how-to-delete-all-local-git-branches)
- [How to undo the last commit from a remote git repository?](#how-to-undo-the-last-commit-from-a-remote-git-repository)
- [How to revert merge?](#how-to-revert-merge)
- [How to revert conflicted merge?](#how-to-revert-conflicted-merge)
- [How to checkout/update a single file from remote origin master?](#how-to-checkoutupdate-a-single-file-from-remote-origin-master)
- [How to pick a commit and apply current branch from another branch? (cherry-pick)](#how-to-pick-a-commit-and-apply-current-branch-from-another-branch-cherry-pick)
- [How to Git cherry-pick only changes to certain files?](#how-to-git-cherry-pick-only-changes-to-certain-files)
- [How to remove untracked files?](#how-to-remove-untracked-files)
- [How to add a message to stash?](#how-to-add-a-message-to-stash)
- [How to bring nth record from the stash list without removing it?](#how-to-bring-nth-record-from-the-stash-list-without-removing-it)
- [How to bring last entry to the stash list and remove?](#how-to-bring-last-entry-to-the-stash-list-and-remove)
- [How to delete a stash record from the list?](#how-to-delete-a-stash-record-from-the-list)
- [How to move latest changes to stash with different branch?](#how-to-move-latest-changes-to-stash-with-different-branch)
- [How to visualize all git logs?](#how-to-visualize-all-git-logs)
- [How to move last commit to another branch?](#how-to-move-last-commit-to-another-branch)
- [How to change last commit message?](#how-to-change-last-commit-message)
- [How to add new changes to the last commit?](#how-to-add-new-changes-to-the-last-commit)


<hr/>

#### How to delete all local git branches?
```bash
git branch --list | grep -v 'master' | xargs git branch -D
```

#### How to undo the last commit from a remote git repository?
```bash
git reset HEAD^
git push origin +HEAD
```

#### How to revert merge?
```bash
# create new branch for being safe.
git revert -m 1 <MERGE_COMMIT_ID>
git push
```

#### How to revert conflicted merge?
```bash
git merge --abort
```

#### How to checkout/update a single file from remote origin master?
```bash
git checkout origin/<branch-name> -- <path-to-file>
```

#### How to pick a commit and apply current branch from another branch? (cherry-pick)
```bash
git cherry-pick <commit_id>
```

#### How to Git cherry-pick only changes to certain files?
```bash
# cherry-pick -n (--no-commit) which lets you inspect (and modify) the result before committing.
git cherry-pick -n <commit>

# unstage everything
git reset HEAD

# stage the modifications you do want
git add <path>

# make the work tree match the index
# (do this from the top level of the repo)
git checkout .
```

#### How to remove untracked files?
```bash
git ls-files --others --exclude-standard | xargs rm
```

#### How to add a message to stash?
```bash
git stash save "Your stash message"
```

#### How to bring nth record from the stash list without removing it?
 ```bash
 git stash apply {n} # n is optional, from nth history.
 ```

#### How to bring last entry to the stash list and remove?
 ```bash
 git stash pop 
 ```

#### How to delete a stash record from the list?
 ```bash
 git stash drop 
 ```

#### How to move latest changes to stash with different branch?
 ```bash
 git stash branch <new-branch-name>
 ```

#### How to visualize all git logs?
 ```bash
 git log --oneline --graph --decorate --all
 ```

#### How to move last commit to another branch?
 ```bash
 # undo the last commit and leave the your changes available
git reset HEAD~ --soft
git stash
# move to the correct branch
git checkout name-of-the-correct-branch
git stash pop
 ```

#### How to change last commit message?
 ```bash
git commit --amend
 ```

#### How to add new changes to the last commit?
 ```bash
# make your change
git add . 
git commit --amend --no-edit
# !!NEVER AMEND PUBLIC COMMITS!!
 ```

