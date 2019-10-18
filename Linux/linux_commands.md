# Linux Commands

## General commands

- `touch`
    - Make an empty file
    - example
        ```
        $ touch CATKIN_IGNORE
        ```

- `grep`
    - `grep -i` : without distinguishing lower case and upper case
    - `grep -n` : Display row numbers
    - `grep -C` : Display the searched word with lines before and after
        ```
        $ grep -C <line number> <word>
        ```
    - `grep -A` : --after-context
    - `grep -B` : --before--context

- `find`
    - `find . -name <filename>` : Find a file called <filename> in the current and sub-directories.

## System Information commands

- `cat /proc/cpuinfo`
- `cat /proc/meminfo`
- `df -h`
- `export -p | less`