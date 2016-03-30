# Removing a file from repository

## Introduction

* Removing a file from repository is done in two steps.
* First you remove the file in the staging area.
* Next you have to commit your changes.
* Directories are not tracked by _GIT_.
  * Once a directory becomes empty it will be discarded.
  * This can be a difference compared to TFS. If you would keep a folder
    for some reason create a ```.gitattribute``` file inside.

## Commands

* First remove the file in staging area:
```
git rm .\MyConsoleApp\console.txt
```
* Check how the status on command line changed.
* Since the ```MyConsoleApp``` should be empty it should disappear from
  disk:

```
ls -l .
```

```
    Directory: D:\Code\GitTraining1


Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         3/17/2016  12:58 PM            MyWindowsApp
-a---         3/17/2016   1:02 PM         45 README.md
```
* Check how the staging area looks like:

```
git status
```

```
D:\Code\GitTraining1 [master +0 ~0 -1]> git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        deleted:    MyConsoleApp/console.txt
```
* Now commit your changes:

```
git commit -m 'Removal of console application'
```

## Comments

* If you would undo the file deletion prior to commit you can use   
  following set of commands:

```
git reset HEAD
git checkout -- MyConsoleApp/console.txt
```

* Commands above will discard the removal from the staging area and then
  restore the file from _GIT_.
