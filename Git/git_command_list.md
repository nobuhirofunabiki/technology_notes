- git add
  - git add -p (--patch)
  - git add .
  - git add -A

- git diff
  - git diff (= git diff HEAD)
  - git diff --cached
  - git diff master origin/master

- git fetch
  - git fetch
  - git fetch origin
  - git fetch --all
  - git fetch -p (= git fetch --purge)

- git log
  - git log --oneline
  - git log --graph
  - git log -p -3

- git merge
  - git merge FETCH_HEAD

- git stash
  - git stash -p
  - git stash apply stash@{}
  - git stash clear
  - git stash list
    - git stash list -p
  - git stash pop stash@{}
  - git stash save (= git stash)
  - git stash show -p stash@{}

- git reset
  - git reset HEAD filepath