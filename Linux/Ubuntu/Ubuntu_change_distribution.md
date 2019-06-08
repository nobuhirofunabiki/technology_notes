#

## Before starting the upgrade of Ubuntu version
Update the packages by the following commands.
```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt dist-upgrade
```
Check the current version of Ubuntu.
```
$ cat /etc/lsb-release
```
Install the `update-manager-core` if it's not installed.
```
$ sudo apt install update-manager-core
```
Check the configuration of `update-manager-core`. In the configuration, `Prompt` should be defined as `lts` or `normal`.
```
$ cat /etc/update-manager/release-upgrades
```

## 

```
$ sudo do-release-upgrade -d
```

## References
- https://qiita.com/TsutomuNakamura/items/bbd712e3afe5f4bacfac
- https://qiita.com/hirotatsuuu/items/e2e47b033dba95bfcf80
- https://yoshinorin.net/2018/08/22/ubuntu1604-upgrade-to-1804/


