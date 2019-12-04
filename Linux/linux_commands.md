# Linux Commands

## General commands

- `touch`
    - Make an empty file
    - example
        ```
        $ touch CATKIN_IGNORE
        ```
- `du`
    - Check the disk usage
    - `du -h` :`du --human-readable`
    - `du -d N` :`du --max-depth=N`
    - (ex) `du -h -d 1`

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

-  `dpkg`
    - `dpkg -l` : Check the version of a installed package
        - ex) `dpkg -l *boost*`

## System Information commands

- `cat /proc/cpuinfo`
- `cat /proc/meminfo`
- `df -h`
- `export -p | less`

## Shutdown Commands

- `shutdown`
    - `shutdown -h`: Turn off the system
        - `shutdown -h now`
        - `shutdown -h +1`: showdonw the system in 1 minute
    - `shutdown -r`: Reboot the system
        - `shutdown -r now`