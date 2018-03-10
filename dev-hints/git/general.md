# General

#### Untrack files

    git rm --cached <file pattern>

    git rm --cached *.pyc

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