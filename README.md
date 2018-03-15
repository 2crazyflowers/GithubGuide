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

To store our staged changes we run the commit command with a message describing what we've changed. Let's do that now by typing: 
 

#### To remove files from the staging area: git reset HEAD filename

git commit -m “Message” - commits the files to the repository along w/ the brief message about the commit, include useful message abt what changed


#### To link to a GitHub Repository:


Create repository on GitHub

Do init and commit like usual

git remote add origin http://github.com/userName/repoName — links to the repo

git push -u origin master — use -u origin master the first time you push to create the master branch

To check status: git remote -v 

To push local changes to the GitHub repo, need to use git push origin master

Forking a repository creates a copy of the GitHub repo under your account

This allows you to make changes without affecting the code in the original repo

The use the Clone/Download button to get the URL to download the repo onto your computer

In your local computer’s terminal, navigate to the desired folder, then

git clone http://github.com/projectURL

Use init, add & commit to save changes locally, but need to use push to move them to GitHub

TO TURN IN PRIME ASSIGNMENTS: COPY AND PASTE THE URL FOR YOUR FORK REPO FOR THE ASSIGNMENT

Use the command atom fileName inside the directory where the file lives to open the file in Atom and load the other project files in the file browser


### Backtracking in Git


The commit you’re currently in is called the HEAD commit

To show it: git show HEAD

To restore the file in your working directory back to the last commit
git checkout HEAD filename
Need to include the filename in the command!!

To check for changes, use: git diff

Print out git commit log: git log
-p — shows the differences introduced in each commit
-2 — limits the log to the last two entries
- -stat — shows abbreviated stats for each commit

To reset back to a specific git commit, you’ll need the first 7 characters of that commit’s SHA
Git reset SHA 

### Branching in Git


Changes made to branches do not affect the master branch until you merge the branch back into the master

git branch — tells you which branch you’re on (indicated by a asterisk)

To create a new branch: git branch new_branch

To switch to a branch: git checkout branch_name

Now all commits will go with this branch and not affect the master branch

An asterisk will indicate which branch you’re on when you type git branch

To merge a branch back into master: git merge branch_name

The branch you’re about to merge into master is the giver branch

The master branch is the receiver branch

YOU NEED TO BE IN THE MASTER BRANCH BEFORE TYPING IN THE MERGE COMMAND (git checkout master)

Merge conflict == when you merge a branch into the master which has had subsequent changes made since you created the branch

Git uses marking to indicate the HEAD (master) version of the file and the branch version of the file).  [See below] 

It then asks us which version of the file to keep.  Make any changes and be sure to delete any markings git adds to the code editor.

To delete a branch: git branch -d branch_name

Make sure the master branch has all the changes you want first!


### Cloning a git repo and working remotely


To clone a git repo: git clone remote_location clone_name

remote_location = where to find the repo (web address, file path, etc.)

clone_name = name to give to the directory in which Git will clone the repo

Git names the remote_location: origin for future reference

To view the git project’s remotes using: git remote -v

To retrieve changes made to the remote repo: git fetch

To integrate changes from remote repo into your local master branch: git merge origin/master

To push changes to the remote repo: git push origin your_branch_name: git push origin master if working with the main branch
 

