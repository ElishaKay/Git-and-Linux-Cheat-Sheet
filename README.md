Save time with these helpful tips!

<h3>How do I remove a big file wrongly committed in git?</h3>

```
git filter-branch --tree-filter 'rm -rf path/to/your/file' HEAD
```
source: https://stackoverflow.com/questions/8083282/how-do-i-remove-a-big-file-wrongly-committed-in-git


<h3>How to replace master branch in Git, entirely, from another branch</h3>

You should be able to use the "ours" merge strategy to overwrite master with seotweaks like this:

```
git checkout seotweaks
git merge -s ours master
git checkout master
git merge seotweaks
The result should be your master is now essentially seotweaks.

```
(-s ours is short for --strategy=ours)


<h3>Deploying / Re-deploying to Heroku</h3>

- You can only push to Heroku via the Master branch, therefore, you must merge your changes for the latest working branch into the Master branch before deployment.

```
git checkout master
git merge latest-branch
git push heroku master
```

<h3>Viewing Branches of a Cloned Repository:</h3>

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
git checkout remotes/origin/lecture/121
```
Shablam. You're now viewing that branch on your local machine! nice.

Source: https://gist.github.com/fabianmoronzirfas/4023446

--------------------------------------------------
<h3>Resolving git merge conflicts:</h3>
```
git fetch origin
git pull origin master
```

These 2 commands will pull changes from master into the branch you want to commit. You can then fix things up in your local repo and 
recommit to the branch you want to push

source: https://stackoverflow.com/questions/161813/how-to-resolve-merge-conflicts-in-git

-------------------------------------
Important Git Note: When you git push force to the master branch, it will annihialite commit history on the git website. 
(but the not the branches on the git site)


------------------------------
<h3>Reset all changes after last commit in git:</h3>

First reset the changes
```
git reset HEAD --hard
```
then clean out everything untracked. If you want to keep files that are not tracked due to .gitignore, be careful with this command.

```
git clean -fd
```
-------------
<h3>When you commit to any git "message" screen, just press: </h3>
```
Ctrl-X
```
To save and exit.

"You can use the --no-edit flag to avoid this behavior, but, well, don't. 
Merge commits, like any commits to history, should be well constructed. Your history should be nothing but useful."

-------------------------------------
```
git stash apply
```
--> retreives the changes that were in place when you typed 'git stash'


---------------------------------------------

When trying to solve a merge conflict, it could be that you want to reset your current branch to a previous commit.

First run: 
```
git log
```

This will show you all of your latest commits. Find the hash of the commit you want to revert back to. Then run:

```
git reset --hard 81e08967b2dfbfef09d62ca9e372c47dfba927db
```

The BEST METHOD to overwrite master with the your latest branch. Let's say you have a branch named "showing_images_in_div_branch".
This branch has the neccessary repo - in its entirety. You dont care about ANYTHING within the master branch!

When you're on the branch called "showing_images_in_div_branch"

```
git merge master --strategy=ours
```

This allows you to merge to master while automatically choosing to overwrite master files with branch

source: https://stackoverflow.com/questions/1295171/git-merge-to-master-while-automatically-choosing-to-overwrite-master-files-with

______________________________________

How to edit lubuntu brightness:

1: cd /sys/class/backlight/intel_backlight

2:  sudo vim brightness 

______________

Start Xampp:

sudo /opt/lampp/lampp start

OR (if mysql is also installed separately on the machine)

sudo service mysql stop
sudo /opt/lampp/lampp start

Stop Xampp:

sudo /opt/lampp/lampp stop
---------------------------

Running MongoDB:

sudo service mongodb start

_________________________

If you want to access an earlier version of  a repo created by someone else:

a) Clone the repo

b) run: 

```
git log --pretty=format:"%h %s" --graph
```

You can hold down the enter key in order to scroll down all the commit history (only shows one line per commit :)

c) You now need to create a Branch from a previous commit. You can create the branch via the commit's hash:

```
git branch branchname <sha1-of-commit>
```

Next, just checkout the branch by running: git checkout branchnam

OR, you can checkout the branch when creating it, using:

```
git checkout -b branchname <sha1-of-commit or HEAD~3>
```
----------------------------------------------------------------------------

<h3>To return the repo (on master) to a previous commit</h3>

The "Already up-to-date" message shows up when the HEAD of the branch you are merging into is a parent of the chain of commits of the branch you want to merge. That's the case, here: D is a parent of E.

```
git reset --hard H (h is the hash of the former branch you want to restore)
```

---------------------------------

<h3>Disable Sleep Mode on Ubuntu</h3>

On Ubuntu 16.04 LTS, I successfully used the following to disable sleep mode:
```
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

And this to re-enable it:
```
sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target
```
