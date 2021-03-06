# General

## Branch

#### Show branches that was merged to another branch

    git branch --merged <branch>

    # Shows branches that is merged to master
    git branch --merged master

#### Show branches that was not merged to another branch

    git branch --no-merged <branch>

    # Shows branches that is not merged to master
    git branch --no-merged master

## Checkout

#### Retrieve a file from a commit

    git checkout <commit> -- <file>

#### Retrieve a deleted from a commit

    git checkout <commit where file was deleted>^ -- file

## Log

#### List commits where a file was modified

    git log --diff-filter=M <path of file>

## Diff

#### View diff of working copy

    git diff --color
    git diff --color <file>

## Stash

#### Stash

    # create stash
    git stash

    # delete stash
    git stash drop

#### Show stashed changes diff

    git stash show -p

#### Include untracked files

    git stash --include-untracked

## Clean

#### Remove all untracked files and directories

    # -d to include directories
    # -f to do cleaning
    git clean -d -f

## Reset

#### Undo a merge using ORIG_HEAD

    git reset --merge ORIG_HEAD

## Config

#### List config

    git config --list

#### Change global user config

    git config --global user.email <email address>

    git config --global user.name <name>

## Special commands

#### Cleanup unnecessary files and optimize the local repository

    git gc

#### Untrack files

This command tags the file as deleted on commit but still retains the history. Use the command `filter-branch` to remove a file completely from history, e.g. sensitive files.

    git rm --cached <file pattern>

    git rm --cached *.pyc

#### Remove sensitive files from history

This command will remove the file from history and also deletes it in the working directory.

    git filter-branch --force --index-filter \
      'git rm --cached --ignore-unmatch <path to sensitive file>' \
      --prune-empty --tag-name-filter cat -- --all

After the command has been executed, force push the branch to remote.

Note: This will not change the timestamp of the commit history.

[Source](https://help.github.com/articles/removing-sensitive-data-from-a-repository/#using-filter-branch)