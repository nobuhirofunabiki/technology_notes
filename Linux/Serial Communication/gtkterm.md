
# gtkterm

## Installation

1. install gtkterm
```
$ sudo apt install gtkterm
```

2. Check the joining groups of the user
```
$ groups ${USER}
```
3. Add a user to `dialout` group
```
$ sudo gpasswd --add ${USER} dialout
```
4. Log-out and log-in 

- If you open gtkterm on the default condition, the following error message appears
```
> Cannot open /dev/ttyS0
```

(reference)
- https://daichiahl.wordpress.com/2016/07/28/ubuntu%E3%81%A7%E3%82%B7%E3%83%AA%E3%82%A2%E3%83%AB%E9%80%9A%E4%BF%A1%E3%81%AE%E3%83%86%E3%82%B9%E3%83%88%E3%82%92%E8%A1%8C%E3%81%86/