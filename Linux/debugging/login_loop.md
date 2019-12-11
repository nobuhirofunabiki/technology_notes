# Linux Login Loop Bug

Ubuntu can be stuck in a login loop. A screen gets black and soon after that, the login screen comes back.

- It is recommended to use `lightdm` instead of `gdm`, but this method didn't work in my case.
- Insead of the above solution, I just installed a few gnome pakcages and this solved the login loop issue. (`chrome-gnome-shell` is not related to this problem.)
```
$ sudo apt remove gnome-settings-daemon
$ sudo apt install gnome-settings-daemon gdm3 gnome-control-center gnome-session
```


(ref)
- https://unix.stackexchange.com/questions/170650/ubuntu-does-no-let-me-log-in-to-my-user-how-can-i-fix-it
- https://askubuntu.com/questions/1119331/how-to-fix-gdm3-login-loop-ubuntu-16-04-lts