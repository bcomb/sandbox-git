# GIT Stickynote
```
// Log
git log --all --graph
git log --pretty=format:"%h %an %ar - %s"
git log --grep="hello"
git log --oneline
git show

// Index status
git status

// Add to index
git add <file0> <file1>

// remove from index
git reset HEAD <file>
or
git restore --staged <file>

// Remove local modification
git checkout <file>
or (since 2.24)
git restore <file>

// Create and switch to branch
git branch <branch>
git checkout <branch>
or
git checkout -b <branch>
or (since 2.24)
git branch <branch>
git switch <branch>
or
git switch -c <branch>

// git fetch
// Fetch downloads the changes from the remote repository into a separate branch named remotes/<remote-name>/<remote-branch-name>.

// git merge  (git merge --abort)
git merge <branch>

// moving/delete/rename
git mv / git rm

// load an external tool of your choice to view the differences
git difftool

// Diff (By default, git diff will only compare the working directory and not the staging area)
git diff
git diff --staged

// GIT Rebasing (checkout the base you want to rebase)
git rebase master
resolve conflict
git add <resolved_file>
git rebase --continue

// GIT STASH
git stash [-u|--include-untracked] [-m <message>]
git stash list
git stash show [-p] 0
git stash apply 0
git stash branch <branch> 0

git stash drop 0    // /!\ can't retrieve this at all
git stash clear     // /!\ can't retrieve this at all

// Remote repository
git remote add origin https://githib.com/test/helloworld.git

git push <remote-repo> <local-branch>
git push origin master

// GIT PULL (git fetch / git merge)
git pull <remote-repo> <local-branch>
git pull origin master
```


Fix a Git detached head?
=====================

Detached head means you are no longer on a branch, you have checked out a single commit in the history (in this case the commit previous to HEAD, i.e. HEAD^).

If you want to *delete* your changes associated with the detached HEAD
-------------------

You only need to checkout the branch you were on, e.g.

`git checkout master`

Next time you have changed a file and want to restore it to the state it is in the index, don't delete the file first, just do

`git checkout -- path/to/foo`

This will restore the file foo to the state it is in the index. 

If you want to *keep* your changes associated with the detached HEAD
-------------------

1. Run `git log -n 1`; this will display the most recent commit on the detached HEAD. Copy-and-paste the commit hash.
2. Run `git checkout master`
3. Run `git branch tmp <commit-hash>`. This will save your changes in a new branch called `tmp`.
4. If you would like to incorporate the changes you made into `master`, run `git merge tmp` from the `master` branch. You should be on the `master` branch after running `git checkout master`.

Memo
=====================
`git submodule add https://github.com/nothings/stb.git ThirdParty/stb`

`git submodule init`

`git submodule update`
