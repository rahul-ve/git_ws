## Git Basics <!-- omit in toc -->


- [Resources](#resources)
- [What is a git repository](#what-is-a-git-repository)
- [Config](#config)
- [Check git version  (keep it current)](#check-git-version--keep-it-current)
- [First time use config](#first-time-use-config)
- [Git init](#git-init)
- [Git add](#git-add)
- [Git commit](#git-commit)
- [Git push](#git-push)
- [Git pull](#git-pull)
- [Branch operations](#branch-operations)
- [Git diff](#git-diff)
- [Git rm](#git-rm)
- [Undoing](#undoing)

#### Resources

- Official Manual – [Git - Reference (git-scm.com)](https://git-scm.com/documentation)
- [Pro Git book](https://git-scm.com/book) (free and kept current, use the web version)
- [VSCode version control docs](https://code.visualstudio.com/docs/editor/versioncontrol)
- [Git cheat sheet](https://training.github.com/downloads/github-git-cheat-sheet.pdf)
- [Short video snippets on how to use VSCode source control](https://www.youtube.com/c/Code/search?query=source%20control)



#### What is a git repository

- A Git repository (repo) is nothing more than a folder, the only difference between a git repo and normal folder is the presence of a hidden `.git` folder within the repo. This folder is where git stores the repo history. If this folder is deleted, the repo history is lost.


&nbsp;

We will go through the below in the workshop

&nbsp;


#### Config

- **.gitconfig file, it should be in your home directory, C:\Users\firstlast\\.gitconfig**

Add the below config to the file, make sure to update the fields:

- name
- email
- excludesfile  - create this file if it does not exist, see next section! Make sure the **filepath** is correct


```
[user]
    name = firstlast
    email = firstlast@example.com
[log]
  date = relative

[alias]
    plog = log --graph --decorate --pretty=format:\"%C(yellow)%h %C(green)%cr %C(blue)[Committer::Author]: %C(blue)%cn::%an %C(auto)%d %C(auto)%s\"

[core]
    excludesfile = C:\Users\firstlast\.gitignore_global
    editor = code --wait

[merge]
    tool = vscode-merge
[mergetool "vscode-merge"]
    cmd = code --wait $MERGED
[diff]
    tool = vscode-diff
[difftool "vscode-diff"]
    cmd = code --wait --diff $LOCAL $REMOTE

```

- **.gitignore_global,  it should be in your home directory, C:\Users\firstlast\\.gitignore_global    (create this file if it does not exist)**

_Any file or folder in any git repo on the system that starts with `gig` will be automatically ignored by git!_

**NOTE - This prefix is arbitrary, pick something that is unique to avoid accidentally excluding files/folders from git tracking.**

Read more about [gitignore](https://git-scm.com/docs/gitignore) in the official docs.

Add the below to the file
```
gig*
```


#### Check git version  (keep it current)
```
 git --version         # update if not current, some of the below commands/options will not work on old versions of git
```

#### First time use config

```
 git config --global user.name "first.lastname"
 git config --global user.email first.last@example.com

# check
 git config --list

```

#### Git init

```
# change to the folder where you want to place the repo
cd \path\to\my\parent_folder

# create a folder
mkdir <folder_name>              # e.g.: mkdir test

# change to the folder
cd \path\to\my\repo_folder         # e.g.: cd test

# initialize the folder as  a git repo
git init -b main               # initializing an empty git repository with the branch name as main

```


#### Git add

```
# add a file to index
git add  <filename>

# use the below with caution, might pick up files with sensitive information
git add  .                            #  stages new files & modifications (no deletions)
git add -A                             # stages all changes, including deletions
git add -u                           # stages files modified & deleted

git  add  somefile*           # use wildcard characters to pick-up files with a pattern
git add  somefolder\*.py              # pick up files with "py" extension  in a subfolder


# we can stage hunks individually, patch mode
git add -p

# do interactive adding
git add -i

```


#### Git commit

```
git commit -m "some descriptive msg"
git commit                                  # this will open a text editor (if configured) to enter the commit message

git commit -i                               # interactive mode, similar to the one used with git-add
git commit -p                               # patch mode, similar to the one used with git-add

# amend a commit
git commit --amend

```



#### Git push

```
# set the remote repo url
git remote add origin  <REMOTE_URL>


# fist push to a remote git hosting service
git push -u origin main                     # push local branch "main" to remote (origin is the default name given to remote repo) and tracks it

# subsequent uploads
git push                                # no need to specify which remote and branch to push, most of the times there will only be one remote.

```

#### Git pull

```
git pull          # to bring in changes from remote repo

```


#### Branch operations

- git branch
- git switch
- git checkout

```
git switch -c  branch1                 # this will create a new branch "branch1" from the current branch,
git checkout -b branch1           # does the same as above, was the old way of doing the above operation,
                                   #  checkout also helps updated files in the working tree to match either index/remote,
                                   # switch is purely for branch operations


git switch  somebranch             # switch to a different branch, NOTE if the local branch does not exist, and if a branch exists upstream,
                                   # it will create a local branch and set it to track upstream branch (see --guess option in the manual)

# NOTE - above behavior is consistent with how git-checkout works
i.e.,  git checkout -b <branch> --track <remote>/<branch>

git switch -                                  # toggle between two branches

# rename a branch
 git branch -m <newname>                         # change the current branch name
 git branch  -m <currentname> <newname>           # change any branch name


 git branch  -v                           # lists all your branches, -v is for verbose, can be stacked for more info
 git branch -a -vv                     # list all branches , more info due to -vv
 git branch -r  -vv                      # list remote branches only


# delete a branch
git branch -d <branch name>              #  has to be merged either upstream or HEAD



```


#### Git diff

```
git diff                        # between working tree and index
git diff --staged              # OR --cached    -   between index and commit tree (i.e., last commit  OR HEAD)
git diff    HEAD                # between working dir and commit tree/HEAD


git diff commit1 commit2          # diff two commits
git diff branch1..branch2         # diff two branches, order matters!!, use option --name-status
git diff branch1                  # same as above, but instead of branch2, HEAD is used, ie, git diff branch1..HEAD

```


#### Git rm

```
git rm --cached file1.txt                     # deletes the file from git NOT file system
git commit -m "remove file1.txt"

git rm file1.txt                               # CAUTION -  deletes the file from both git and file system
git commit -m "remove file1.txt"

```

#### Undoing


- git-revert is about making a new commit that reverts the changes made by other commits.
- git-restore is about restoring files in the working tree from either the index or another commit. This command does not update your branch. The command can also be used to restore files in the index from another commit.
- git-reset is about updating your branch, moving the tip in order to add or remove commits from the branch. This operation changes the commit history.
git reset can also be used to restore the index, overlapping with git restore

NOTE - read [7.7 Git Tools - Reset Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)


```

# revert a commit, NOTE HEAD~ stands for parent of current commit, HEAD~3 is the 3rd ancestor

git reset --soft HEAD~                  # move the HEAD back by one commit
git reset --mixed HEAD~            # move the HEAD back by one commit and reset Index as well
git reset --hard  HEAD~              # resets all three trees, CAUTION, this will cause data loss if used incorrectly

# undo changes to a file

git restore --staged --worktree -- filename           # use --source option to specify where to get the file from

# IF UNDOING BY USING restore, use the -p/--patch option, to selectively revert file contents!


```
