# Linux Commands

## General commands (Pre-installed)

- `dpkg`
    - dpkg: Debian Package
    - `dpkg -l` : Check the version of a installed package
        - ex) `dpkg -l *boost*`

- `du`
    - Check the disk usage
    - `du -h` :`du --human-readable`
    - `du -d N` :`du --max-depth=N`
    - (ex) `du -h -d 1`

- `find`
    - `find . -name <filename>` : Find a file called <filename> in the current and sub-directories.

- `free`
    - display the total amount of fre space available along with the amount of memory used and swap memory in the system
    - examples
        - `free -m (/-g)`
        - `free -h`

- `grep`
    - `grep -i` : without distinguishing lower case and upper case
    - `grep -n` : Display row numbers
    - `grep -C` : Display the searched word with lines before and after
        ```
        $ grep -C <line number> <word>
        ```
    - `grep -A` : --after-context
    - `grep -B` : --before--context

- `less`
    - to read contents of a text file one page per time for the faster access

- `sort`
    - sort a file, arranging the records in a particular order
    - `sort -n`: sort a file numerically
    - `sort -r`: sort a file in a reverse order
    - example
        - `du -a / | sort -nr | head -n 10`

- `touch`
    - Make an empty file
    - example
        ```
        $ touch CATKIN_IGNORE
        ```
- `watch`
    - execute a program periodically (every 2 seconds by default), showing output in fullscreen
    - example
        - `watch -n 1 free -h`

## Commands which need to be installed

- `tree`
    - `$ sudo apt install tree`
    - a recursie directory listing program that produces a depth-indented listing of files
    - exmaples
        - `tree -d`: List directories only
        - `tree -f`: Print the full path prefix for each file
        - `tree -d -f | grep hogehoge_*`

## System Information commands

- `cat /proc/cpuinfo`
- `cat /proc/meminfo`
- `df -h`
- `export -p | less`

## Apt commands

- `sudo apt update`
    - This command is used to download package information from all configured sources (resynchronize the package index files from their sources).
    - The sources are often defined in `/etc/apt/sources.list` file and other files are located in `etc/apt/sources.list.d` directory.
- `apt list --upgradable`
- `sudo apt upgrade`
    - Install available upgrades of all packages currently installed on the system from the sources configured via sources.list file.

## Shutdown Commands

- `shutdown`
    - `shutdown -h`: Turn off the system
        - `shutdown -h now`
        - `shutdown -h +1`: showdonw the system in 1 minute
    - `shutdown -r`: Reboot the system
        - `shutdown -r now`
        - You can reboot the system by the following command
            - `sudo reboot`

## Others

- How to empty the trash box?
    - `$ cd ~/.local/share/Trash/files`
    - `$ rm -rf *`