# Git stuff
- A line with `$` represents a command to run in the command line. 
## Helpful commands
- `$ git pull`: updates local repo with remote changes
- `$ git status`: tells you the "status" of you repo (your current branch, changes ready to be commited, tracked and untracked changes).
- `$ git diff`: will tell you line by line changes you have made that aren't added to index (uncommmitted changes).
- `$ git add <directory/file>`: "stages" changes made in `<directory/file>`. (Lets git know the files that you want to update.)
- `$ git commit`: or `$ git commit -m "<commit message>"` locally commits changes. Ready to be pushed to remote repo.
- `$ git push`: updates the remote repo with your changes. Will cause a merge error if there are remote chagnes that you don't have locally. 
- `$ git fetch`: similar to get pull, but does not merge remote changes with local changes. Can be helpful if you want to run `$ git diff main..origin/main` to see the differences between your repo and remote repo. 
- `$ git branch <name>`: makes a new branch off the branch you're currently on.(might make an example for this sometime.)
- `$ git checkout <branch name>`: switches your directory to the branch specified by `<branch name?>` 
- `$ git checkout <directory/file> <commit hash>`: will change file specified by `<directory/file>` to the version at the commit sepcified by `<commit hash>`. Get the hash by doing `$ git log` or going to github and finding the hash. 
- `$ git log`: shows all recent commits and related info.

## Getting Started (see Example 1)
1. Navigate to wherever you want to put the repo
2. `$ git clone <web address of repo>`
    - git will only see the changes you make inside of this repo

## Update a repo with your local code (Example 2)
1. `$ git pull`: updates your repo with remote repo 
    - `git pull` is the same as running `$ git fetch` then immediately running `$ git merge`. 
2. `$ git add <filename or directory>`: This "stages" the changes to the files to be commited
    - any changes made to the file after being running this command are not tracked until they are `$ git add`'ed again. 
3. `$ git commit`: adds you changes to the repo. Will ask for a commit message.
    - These changes are only tracked locally. The remote repo has no idea that you've made any changes yet!
    - One liner for commit and message: `$ git commit -m "<your commit message>"`
4. `$ git push`: updates the remote repo with your committed changes. 

## When does a merge happen? 
Luke and Trevor begin by updating their repos with `$ git pull`. Luke and Trevor make edits and commit their changes. Luke pushes his changes to the remote repo. Trevor pushes his changes to the remote repo, but git tells him that he can't because there are remote changes that he doesn't have locally. Trevor runs `$ git pull` and a merge happens. If Luke and Trevor modified different files, the merge will happen pretty much automatically. If there are lines of code that both Trevor and Luke both edited, Trevor will have to resolve a merge conflict and commit his changes once he's happy with his changes. See [this link](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line) for more info on resolving merges. 




# Examples
- These examples use git bash. It should installed by deafult when you install git. The following example should be the same if using Mac Terminal or Windows Powershell.

- The lines that say `C:/Users/luker....` above your command tells you what directory you're in

### **Example 1**: Getting started
``` bash 
C:/Users/luker
$ ls # lists all the files and folders in current directory
"Desktop/
 Documents/
 Downloads/
 Favorites/
 Links/" 

C:/Users/luker
$ cd Documents/ #cd = change directory

C:/Users/luker/Documents
$ ls # lists all the files and folders in current directory
"Arduino/                    MATLAB/                  QMK/
'Assetto Corsa'/            'My Games'/              'Sound recordings'/
'Calibre Library'/          'My Music'@               Zoom/
'Custom Office Templates'/  'My Pictures'@            controls/
FeedbackHub/               'My Videos'@              desktop.ini
Lightshot/                 'New Text Document.txt'"

C:/Users/luker/Documents
$ git clone 'https://github.com/ASEN-SAILR/controls'
Cloning into 'controls'...
remote: Enumerating objects: 31, done.
remote: Counting objects: 100% (31/31), done.
remote: Compressing objects: 100% (23/23), done.
remote: Total 31 (delta 8), reused 25 (delta 5), pack-reused 0
Receiving objects: 100% (31/31), 3.69 MiB | 8.15 MiB/s, done.
Resolving deltas: 100% (8/8), done.

C:/Users/luker/Documents
$ cd controls

C:/Users/luker/Documents/controls 
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
``` 

### **Example 2**: Commit and push changes
```bash
C:/Users/luker/Documents/automation
$ git pull #updates local repo with remote changes
"remote: Enumerating objects: 18, done.
remote: Counting objects: 100% (18/18), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 16 (delta 5), reused 15 (delta 4), pack-reused 0
Unpacking objects: 100% (16/16), 5.83 KiB | 221.00 KiB/s, done.
From https://github.com/ASEN-SAILR/automation
   6ba2771..7b6c463  main       -> origin/main
Updating 6ba2771..7b6c463
Fast-forward
 .DS_Store                         | Bin 0 -> 6148 bytes
 gps/.DS_Store                     | Bin 0 -> 6148 bytes
 gps/GPSfunctions.py               |  96 ++++++++++++++++++++++++++++++++++++++
 gps/arduino2csv.py                |  40 ++++++++++++++++
 gps/gps_read/.DS_Store            | Bin 0 -> 6148 bytes
 gps/gps_read/gps_read.ino         |  59 +++++++++++++++++++++++
 gps/gps_read_raw/gps_read_raw.ino |  52 +++++++++++++++++++++
 gps/plot_gps.m                    |  59 +++++++++++++++++++++++
 8 files changed, 306 insertions(+)
 create mode 100644 .DS_Store
 create mode 100644 gps/.DS_Store
 create mode 100644 gps/GPSfunctions.py
 create mode 100644 gps/arduino2csv.py
 create mode 100644 gps/gps_read/.DS_Store
 create mode 100644 gps/gps_read/gps_read.ino
 create mode 100644 gps/gps_read_raw/gps_read_raw.ino
 create mode 100644 gps/plot_gps.m"

C:/Users/luker/Documents/automation
$git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   lidar/lidar_test2.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        scan_data.npy

no changes added to commit (use "git add" and/or "git commit -a")
```
Above, you can see that I have two files that git sees within my repo. 
- `lidar/lidar_test2.py` is a file that git is "tracking". This means that this git repo has a version of this file and can tell that I made an update to it. 
- `scan_data.npy` is a file that the repo is not tracking. That means that unless I run `$ git add scan_data.py`, git does not have a version of this file. This either means that it is a new file that I want to add to the repo, or is a file that I never want to be tracked by git.  

At this point, if I run `$ git commit`, nothing will happen because nothing has been added to the "index" to be added. Git will just be confused and give me the same output as `$ git status`. 

In order to add my updates to be committed, I need to run `$ git add`. You can either specify a single file or a whole directory using `git add .` but be careful when adding a whole directory, because this may add unwanted files to be committed (such as the scan_data.npy). 
``` bash
C:/Users/luker/Documents/automation
$ git add lidar/lidar_test2.py #adds just the one file

C:/Users/luker/Documents/automation
$ git status 
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   lidar/lidar_test2.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        scan_data.npy

# lidar/lidar_test2.py was added to the "index" and is ready to be commited
C:/Users/luker/Documents/automation
$ git commit -m "increased buffer size" 
[main 14b029a] increased buffer size
 1 file changed, 1 insertion(+), 1 deletion(-)

#now I can push my changes
C:/Users/luker/Documents/automation
$ git push 
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 378 bytes | 378.00 KiB/s, done.
Total 4 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To https://github.com/ASEN-SAILR/automation
   7b6c463..14b029a  main -> main

C:/Users/luker/Documents/automation
$ git status #one last git status for good measure
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        scan_data.npy

nothing added to commit but untracked files present (use "git add" to track)
```
