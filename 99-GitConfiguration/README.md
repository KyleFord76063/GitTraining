# Configuration

## Introduction

* _GIT_ stores the configuration in ```gitconfig``` files.
* Configuration file define also the user's name and email which
  is being used during ```git-commit```.
* There are three levels of configuration:
  * system
    * Machine specific, shared with all users.
    * To edit the file in plain text you can use:

```
git config --system --edit
```

  * global
    * User specific, shared by given user for all repositories.
    * Overrides _system_ level.
    * To edit the file in plain text you can use:

```
git config --global --edit
```
  * local
    * Repository specific.
    * Overrides _global_ and _system_ level.
    * To edit the file in plain text you can use:

```
git config --local --edit
```

## E-mail and user name configuration

* Two commands below will set user's email and user name on global level.
* This means that unless the cloned repository have a local override
  these values will be used.
* It is very handy if you work on multiple repositories.
* You can always user ```--local``` instead of ```--global``` to override
  values per repository.
* File should be located as ```.gitconfig``` in your home directory.

```
git config --global user.email "your_email@example.com"
```

```
git config --global user.name "Vladimir Kloz"
```

## Merge tool

* It is pretty handy to use a visual merge tool you are used to use.
* For 3-way merge Visual Studio works pretty well.
* Open the global configuration file:

```
git config --global --edit
```

* Copy & Paste lines below to it (obviously adjust paths if/as needed
  to match your VS version/location):

```
[merge]
      tool = vsdiffmerge
[mergetool]
      prompt = false
      keepbackup = false
[mergetool "vsdiffmerge"]
      cmd = '"C:/Program Files (x86)/Microsoft Visual Studio 12.0/Common7/IDE/vsdiffmerge.exe"' "$REMOTE" "$LOCAL" "$BASE" "$MERGED" //m
      trustexitcode = true
```

* Save the file.

## Diff tool

* For the comparison (diff) it is good to use a tool you are used to.
* Example below shows how to setup [Winmerge](http://winmerge.org/downloads/).
* Open the global configuration file:

```
git config --global --edit
```

* Copy & Paste lines below to it:

```
[diff]
    tool = winmerge
[difftool "winmerge"]
    cmd = winmergeu.exe -e -ub -x -wl -u -maximise -dl "base" -dr "mine" \"$LOCAL\" \"$REMOTE\"
[difftool]
    prompt = false
```

* Save the file.

## Default text editor

* Another handy setting can be the default text editor which opens during
  various operations.
* Command below uses _notepad++_ but can be adjusted easily to anything
  else.

```
git config --global core.editor "'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```
