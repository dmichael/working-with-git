# Working with git

Some common commands for managing git like a boss


## `rebase`

* Moves all your local commits to the top of the history of the merged branch. This is different than `merge` which interleaves commits based on timestamps.

```
git rebase origin/master
```

This pulls from remote master and rebases the current local branch from origin/master. It DOES NOT update local master.
```
git pull --rebase origin master
```

## Difference between `origin/master` and `origin master`

This difference of syntax can be the cause of some confusion. [This StackOverflow question](https://stackoverflow.com/questions/18137175/in-git-what-is-the-difference-between-origin-master-vs-origin-master) and [this one](https://stackoverflow.com/questions/2883840/differences-between-git-pull-origin-master-git-pull-origin-master) answers the question as follows:

* `origin master` is actually two things, a remote (`origin`) and a branch (`master`). *This is likely the one you want.*
* `origin/master` is a local copy of a the remote branch `master` on `origin` repo. You almost never want this one.

### Here are some examples
```bash
git pull origin master
```
* Pull the latest from remote master and merge it in your current branch. 
* Add --rebase to rebase instead of merge.
* What this is doing under the covers is a `git fetch origin master && git merge origin/master`.

```
git pull origin/master
```
* Pull from your local copy of `master` at `origin`, and merge it into the current branch

## References

* `rebase` - https://nathanleclaire.com/blog/2014/09/14/dont-be-scared-of-git-rebase/
