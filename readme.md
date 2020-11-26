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
