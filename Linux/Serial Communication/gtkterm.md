
# gtkterm

## Installation

1. install gtkterm
```
$ sudo apt install gtkterm
```

2. Check the joining groups of the user
```
$ group ${USER}
```
3. Add a user to `dialout` group
```
$ sudo gpasswd -add ${USER} dialout
```
4. Log-out and log-in 

- If you open gtkterm on the default condition, the following error message appears
```
> Cannot open /dev/ttyS0
```