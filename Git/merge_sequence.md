# Typical Merge Sequence

- pull the target branch(ex. master) from the remote repository
```
@ master 
$ git pull
```
- cut the target branch from the target branch on the local repository
```
@ master
$ git checkout -b feature/<branch_name>
@ feature/<branch_name>
```
- merge the feature branch to the branch cut from the cut from the target branch
```
@ feature/<branch_name>
$ git merge master
```
- edit the files and solve the conflicts
- git add and commit
```
@ feature/<branch_name>
$ git push origin feature/<branch_name>
```
- send the merge request on the remote repository

