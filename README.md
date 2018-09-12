Viewing Branches of a Cloned Repository:

When you clone a repository, run:

```
git branch -a
```

This will show you all the branches from the remote repo (hidden on your own computer).

The output may look something like this:

```
master
  remotes/origin/HEAD -> origin/master
  remotes/origin/lecture/060
  remotes/origin/lecture/066
  remotes/origin/lecture/068
  remotes/origin/lecture/069
  remotes/origin/lecture/070
  remotes/origin/lecture/072
  remotes/origin/lecture/073
```

To view one of these branches on your local machine, simply discard the word 'remotes/'. Instead, just run something like this.

```
git checkout origin/lecture/121
```
Shablam. You're now viewing that branch on your local machine! nice.

Source: https://gist.github.com/fabianmoronzirfas/4023446

--------------------------------------------------
Resolving git merge conflicts:

git fetch origin
git pull origin master

These 2 commands will pull changes from master into the branch you want to commit. You can then fix things up in your local repo and 
recommit to the branch you want to push

source: https://stackoverflow.com/questions/161813/how-to-resolve-merge-conflicts-in-git

-------------------------------------
Important Git Note: When you git push force to the master branch, it will annihialite commit history on the git website. 
(but the not the branches on the git site)


------------------------------
Reset all changes after last commit in git:

First reset the changes

git reset HEAD --hard
then clean out everything untracked. If you want to keep files that are not tracked due to .gitignore, be careful with this command.

git clean -fd

-------------
When you commit to any git "message" screen, just press: 

Ctrl-X

To save and exit.

"You can use the --no-edit flag to avoid this behavior, but, well, don't. 
Merge commits, like any commits to history, should be well constructed. Your history should be nothing but useful."

--------------

git stash apply

--> retreives the changes that were in place when you typed 'git stash'


---------------------------------------------

When trying to solve a merge conflict, it could be that you want to reset your current branch to a previous commit.

First run: git log

This will show you all of your latest commits. Find the hash of the commit you want to revert back to. Then run:

git reset --hard 81e08967b2dfbfef09d62ca9e372c47dfba927db

The BEST METHOD to overwrite master with the your latest branch. Let's say you have a branch named "showing_images_in_div_branch".
This branch has the neccessary repo - in its entirety. You dont care about ANYTHING within the master branch!

When you're on the branch called "showing_images_in_div_branch"

git merge master --strategy=ours

This allows you to merge to master while automatically choosing to overwrite master files with branch

source: https://stackoverflow.com/questions/1295171/git-merge-to-master-while-automatically-choosing-to-overwrite-master-files-with

______________________________________

How to edit lubuntu brightness:

1: cd /sys/class/backlight/intel_backlight

2:  sudo vim brightness 

______________

Start Xampp:

sudo /opt/lampp/lampp start

Stop Xampp:

sudo /opt/lampp/lampp stop
---------------------------

Running MongoDB:

sudo service mongodb start

_________________________

If you want to access an earlier version of  a repo created by someone else:

a) Clone the repo

b) run:   git log --pretty=format:"%h %s" --graph

You can hold down the enter key in order to scroll down all the commit history (only shows one line per commit :)

c) You now need to create a Branch from a previous commit. You can create the branch via the commit's hash:

git branch branchname <sha1-of-commit>

Next, just checkout the branch by running: git checkout branchnam

OR, you can checkout the branch when creating it, using:

git checkout -b branchname <sha1-of-commit or HEAD~3>

----------------------------------------------------------------------------

To return the repo (on master) to a previous commit

The "Already up-to-date" message shows up when the HEAD of the branch you are merging into is a parent of the chain of commits of the branch you want to merge. That's the case, here: D is a parent of E.

git reset --hard H (h is the hash of the former branch you want to restore)
