---
layout: post
title:  "Git Tutorial"
author: mamin
categories: [ Git, tutorial ]
image: assets/images/16.jpg
---
This is a mini tutorial for Git.

## Initial Git Configuration
Using git config with the --global option manages the default settings for all Git projects to which you contribute by saving the settings in your ~/.gitconfig file.

```bash
[user@host ~]$ git config --global user.name 'Mudassar Ali'
[user@host ~]$ git config --global user.email mamin@example.com
```

## Modify shell prompt
To modify your shell prompt in this way, add the following lines to your ~/.bashrc file:

```bash
source /usr/share/git-core/contrib/completion/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=true
export GIT_PS1_SHOWUNTRACKEDFILES=true
export PS1='[\u@\h \W$(declare -F __git_ps1 &>/dev/null && __git_ps1 " (%s)")]\$ '
```
If your current directory is in a Git working tree, then the name of the current Git branch for the working tree is displayed in parentheses. If you have untracked, modified, or staged files in your working tree, then the prompt could indicate one of the following meanings:

- (branch *) means that you have modified a tracked file.
- (branch +) means that you have modified a tracked file and used git add to stage it.
- (branch %) means that you have untracked files in your tree.

Combinations of markers are possible, such as (branch *+).

## Git Quick Reference


| Command                  | Description |
|--------------------------|-------------|
| `git clone URL`          | Clone an existing Git project from the remote repository at URL into the current directory. |
| `git status`             | Display the status of files in the working tree. |
| `git add file`           | Stage a new or changed file for the next commit. |
| `git rm file`            | Stage removal of a file for the next commit. |
| `git reset`              | Unstage files that have been staged for the next commit. |
| `git commit`             | Commit the staged files to the local repository with a descriptive message. |
| `git push`               | Push changes in the local repository to the remote repository. |
| `git pull`               | Fetch updates from the remote repository to the local repository and merge them into the working tree. |
| `git revert commit-hash` | Create a commit, undoing the changes in the referenced commit. You can use the commit hash that identifies the commit, although there are other ways to reference a commit. |
| `git init`               | Create a project. |
| `git log`                | Display the commit log messages. |
| `git show commit-hash`   | Shows what was in the change set for a particular commit hash. |

## Git Branch
```
[user@host ~]$ git checkout -b feature/1
Switched to a new branch 'feature/1'

# push branch to remote
[user@host ~]$ git push --set-upstream origin feature/1
```

![Git Branch](/assets/images/versioning-feature-branch.svg)

