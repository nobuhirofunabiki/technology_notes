- git add
  - git add -p (--patch)
  - git add .
  - git add -A

- git branch
  - git branch -m *new_branch_name*
  - git branch -m *old_branch_name* *new_branch_name*

- git cherry-pick
  - git cherry-pick *commit_hash*
  - git cherry-pick -e (--edit) *commit_hash*
  - git cherry-pick -n (--no-commit) *commit_hash*

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
  - git log -p *commit_hash*

- git merge
  - git merge FETCHED_HEAD

- git rev-parse
  - git rev-parse HEAD
    - Return the name of the current commit hash
  - git rev-parse --abbrev-ref HEAD
    - Return the name of the current branch

- git reset
  - git reset HEAD *file_path*
  - git reset --hard HEAD

- git stash
  - git stash -p
  - git stash apply stash@{}
  - git stash clear
  - git stash drop stash@{}
  - git stash list
    - git stash list -p
  - git stash pop stash@{}
  - git stash save (= git stash)
    - git stash save *arbitrary message*
  - git stash show -p stash@{}
  - others
    - git diff stash@{}

- git tag
  - git tag
    - Show the list of the existing tags
  - git push origin *tag_name*
    - A new tag needs to be pushed to a remote repository
  - git tag -a *tag_name* -m *tag_comment* *commit_hash*
    - example
      ```
      @master
      $ git tag -a v1.0 -m 'First release version' HEAD
      ```
  - 
