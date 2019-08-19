# Git ignore

## How to apply git ignore to all the directories

1. Add `.gitignore_global` in the home directory
2. Save it in the git config
    ```
    $ git config --global core.excludesfile ~/.gitignore_global
    ```
3. Check
    ```
    $ git config --list | grep exclude

(ref)
- https://qiita.com/sqrtxx/items/1eb5828a7acd821c3706