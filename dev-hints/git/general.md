# General

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

#### View diff of working copy

    git diff --color
    git diff --color <file>

#### Stash

    # create stash
    git stash

    # delete stash
    git stash drop

#### Show stashed changes diff

    git stash show -p

#### List config

    git config --list

#### Change global user config

    git config --global user.email <email address>

    git config --global user.name <name>
