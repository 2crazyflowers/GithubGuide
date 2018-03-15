# Github Guide

Terminal & Git Notes

### Terminal Commands
cd - change directory

ls - list files and folders

ls -a  — list all files and folders, including hidden ones

pwd - print working director (shows path to current location)  

mkdir - makes a new folder

touch - makes a new file (include extension w/ the name)

rm - removes file

rm -rf  - to remove a folder

mv <file-old> <file-new> — Renames the file

mv <file> <director> — Moves file to directory
 
cp <file> <directory> — Copy file to directory
 
cp <directory1> <directory2> — Copy first directory to a new directory 

clear - clears the terminal window

open . — opens the current folder in the Finder window (dot indicates current folder)

atom . — will open Atom editor and the current folder you’re in


### Git Commands

git argument -flag


#### To set user name & email in the config file:

git config —global user.name “FirstName Last Name”

git config —global user.email “email@youremail.com"


#### To create a Git Repository:

1. Navigate to the folder you want or create a new folder then navigate inside of it

1. On the command line type `git init` — which initializes a new repository inside the folder you’re currently it & git will start tracking the changes you now make

1. Then type `git status` —  which displays status, including any uncommitted files. If a file shows as "untracked" that means Git sees that as a new file.

1. In order to have Git track any changes to the files in your folder you need to *add* the files to the staging area. Once files have been added Git will monitor them for any changes made to them so you know if you need to commit those changes to the online repo. There are two ways to do this: you can either track specific files or you can track the entire folder that Git is connected to:

 * type `git add filename1 filename2` (example - `git add readme.md` ) — this stages a commit, adds the current files in the current folder to the upcoming commit

 * To add the whole folder you are currently in & all files in it type: `git add .`

1. You can then verify that those files/folders are in the staging area by typing `git status`. This should show you the files that you just added in the previous step. Notice how Git says changes to be committed? The files listed here are in the Staging Area, and they are not in our repository yet. We could add or remove files from the stage before we store them in the repository.

1. To remove files from the staging area: `git reset HEAD filename`

1. If you've made changes to files before commiting, you can add all the new files using a wildcard with git add: `git add '*.txt'`

1. To store our staged changes we run the commit command with a message describing the changes you've made. This is done by typing `git commit -m "notes of changes you've made"`. This commits the files to the repository along w/ the brief message about the commit, include useful message about what was changed.


#### Log Files

You can review the changes you have committed by using `git log`. This is like a journal that remembers all the changes we've committed so far, in the order you committed them.



#### To link to a GitHub Repository:

1. Create repository on GitHub

1. Do `git init` and commit like usual

`git remote add origin http://github.com/userName/repoName` — links to the repo

`git push -u origin master` — use -u origin master the first time you push to create the master branch

To check status: `git remote -v` 

To push local changes to the GitHub repo, need to use `git push origin master`


#### Forking a Repository 

This creates a copy of the GitHub repo under your account

It allows you to make changes without affecting the code in the original repo

The use the Clone/Download button to get the URL to download the repo onto your computer

In your local computer’s terminal, navigate to the desired folder, then `git clone http://github.com/projectURL`

Use init, add & commit to save changes locally, but need to use push to move them to GitHub

TO TURN IN PRIME ASSIGNMENTS: COPY AND PASTE THE URL FOR YOUR FORK REPO FOR THE ASSIGNMENT

Use the command atom fileName inside the directory where the file lives to open the file in Atom and load the other project files in the file browser


### Backtracking in Git


The commit you’re currently in is called the HEAD commit

To show it: git show HEAD

To restore the file in your working directory back to the last commit
`git checkout HEAD filename`
Need to include the filename in the command!!

To check for changes, use: `git diff`

Print out git commit log: `git log`
-p — shows the differences introduced in each commit
-2 — limits the log to the last two entries
- -stat — shows abbreviated stats for each commit

To reset back to a specific git commit, you’ll need the first 7 characters of that commit’s SHA
`Git reset SHA`

### Branching in Git


Changes made to branches do not affect the master branch until you merge the branch back into the master

`git branch` — tells you which branch you’re on (indicated by a asterisk)

To create a new branch: `git branch new_branch`

To switch to a branch: `git checkout branch_name`

Now all commits will go with this branch and not affect the master branch

An asterisk will indicate which branch you’re on when you type `git branch`

To merge a branch back into master: `git merge branch_name`

The branch you’re about to merge into master is the giver branch

The master branch is the receiver branch

YOU NEED TO BE IN THE MASTER BRANCH BEFORE TYPING IN THE MERGE COMMAND (`git checkout master`)

Merge conflict == when you merge a branch into the master which has had subsequent changes made since you created the branch

Git uses marking to indicate the HEAD (master) version of the file and the branch version of the file).  [See below] 

It then asks us which version of the file to keep.  Make any changes and be sure to delete any markings git adds to the code editor.

To delete a branch: `git branch -d branch_name`

Make sure the master branch has all the changes you want first!


### Cloning a git repo and working remotely


To clone a git repo: `git clone remote_location clone_name`

remote_location = where to find the repo (web address, file path, etc.)

clone_name = name to give to the directory in which Git will clone the repo

Git names the remote_location: origin for future reference

To view the git project’s remotes using: `git remote -v`

To retrieve changes made to the remote repo: git fetch

To integrate changes from remote repo into your local master branch: git merge origin/master

To push changes to the remote repo: git push origin your_branch_name: git push origin master if working with the main branch

#### Pushing/Pulling with a Group


Other people pulled your changes, made their own commits, and pushed them. You can check for changes on your GitHub repository and pull down any new changes by running: `git pull origin master`

If you see something like this after you've pulled:

Updating 3852b4d..3e70b0f
Fast-forward
 yellow_octocat.txt |    1 +
 1 file changed, 1 insertion(+)
 create mode 100644 yellow_octocat.txt
 
 Then you know there have been some additions and changes to the octocat family. Let's take a look at what is different from our last commit by using the `git diff` command.

In this case we want the diff of our most recent commit, which we can refer to using the HEAD pointer: `git diff HEAD`

diff --git a/octocat.txt b/octocat.txt
index 7d8d808..e725ef6 100644
--- a/octocat.txt
+++ b/octocat.txt
@@ -1 +1 @@
-A Tale of Two Octocats
`+[mA Tale of Two Octocats and an Octodog`

Run `git diff --staged` option to see the changes you just staged. You should see that  octodog.txt was created.

diff --git a/octofamily/octodog.txt b/octofamily/octodog.txt
new file mode 100644
index 0000000..cfbc74a
--- /dev/null
+++ b/octofamily/octodog.txt
@@ -0,0 +1 @@
`+[mwoof`

You can unstage files by using the `git reset filename` command. This unstages octodog.txt, but you'll notice that he's still there. He's just not staged anymore. It would be great if we could go back to how things were before octodog came around and ruined the party.

Files can be changed back to how they were at the last commit by using the command: git checkout -- <target>. Go ahead and get rid of all the changes since the last commit for octocat.txt `git checkout -- octocat.txt`
 
 When developers are working on a feature or bug they'll often create a copy (aka. branch) of their code they can make separate commits to. Then when they're done they can merge this branch back into their main master branch.

We want to remove all these pesky octocats, so let's create a branch called clean_up, where we'll do all the work:

git branch clean_up

Great! Now if you type git branch you'll see two local branches: a main branch named master and your new branch named  `clean_up`.

You can switch branches using the git checkout <branch> command. Try it now to switch to the clean_up branch:

git checkout clean_up
Switched to branch 'clean_up'

Removing All The Things - so you're in the clean_up branch. You can finally remove all those pesky octocats by using the git rm command which will not only remove the actual files from disk, but will also stage the removal of the files for us.

You're going to want to use a wildcard again to get all the octocats in one sweep, go ahead and run:

git rm '*.txt'

rm 'blue_octocat.txt'
rm 'octocat.txt'
rm 'octofamily/baby_octocat.txt'
rm 'octofamily/momma_octocat.txt'
rm 'red_octocat.txt'

Commiting Branch Changes
Now that you've removed all the cats you'll need to commit your changes.

Feel free to run git status to check the changes you're about to commit.

git commit -m "Remove all the cats"

[clean_up a6a3de9] remove all the cats
 5 files changed, 5 deletions(-)
 delete mode 100644 blue_octocat.txt
 delete mode 100644 octocat.txt
 delete mode 100644 octofamily/baby_octocat.txt
 delete mode 100644 octofamily/momma_octocat.txt
 delete mode 100644 red_octocat.txt
Switching Back to master
Great, you're almost finished with the cat... er the bug fix, you just need to switch back to the master branch so you can copy (or merge) your changes from the clean_up branch back into the master branch.

Go ahead and checkout the master branch:

git checkout master
Switched to branch 'master'

Preparing to Merge
Alrighty, the moment has come when you have to merge your changes from the clean_up branch into the master branch. Take a deep breath, it's not that scary.

We're already on the master branch, so we just need to tell Git to merge the clean_up branch into it:

git merge clean_up
Updating 3852b4d..ec6888b
Fast-forward
 blue_octocat.txt             |    1 -
 octocat.txt                  |    1 -
 octofamily/baby_octocat.txt  |    1 -
 octofamily/momma_octocat.txt |    1 -
 red_octocat.txt              |    1 -
 5 files changed, 5 deletions(-)
 delete mode 100644 blue_octocat.txt
 delete mode 100644 octocat.txt
 delete mode 100644 octofamily/baby_octocat.txt
 delete mode 100644 octofamily/momma_octocat.txt
 delete mode 100644 red_octocat.txt
 
 Keeping Things Clean
Congratulations! You just accomplished your first successful bugfix and merge. All that's left to do is clean up after yourself. Since you're done with the clean_up branch you don't need it anymore.

You can use git branch -d <branch name> to delete a branch. Go ahead and delete the clean_up branch now:

git branch -d clean_up

Deleted branch clean_up (was ec6888b).

The Final Push
Here we are, at the last step. I'm proud that you've made it this far, and it's been great learning Git with you. All that's left for you to do now is to push everything you've been working on to your remote repository, and you're done!

git push
To https://github.com/try-git/try_git.git
   3e70b0f..0842f91  master -> master
