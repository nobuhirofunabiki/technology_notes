# Modify commit messages

## Modification on a local repository

### Latest commit
```
$ git commit --amend -m "Modified message"
```

### Past commit

Make use of `git rebase -i` command.
Consider such situation that you want to change the 3rd commit message from `HEAD` commit. 
```
$ git rebase -i HEAD~3
```
In an editor, change the status of the commit message you want to modify from `pick` to `edit`, and exit.
```
$ git commit --amend -m "modified message"
$ git rebase --continue
```
