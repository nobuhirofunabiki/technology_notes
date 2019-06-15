# ROS Logging

## How to see ROS_DEBUG (from a setting file / commandline)

ROS console settings get reset when it's re-launched.

1. Create a file such as
   ```
   $ vim ~/.rosconsole
   ```
2. Inside that file, turn on all debug messages by adding the following line
   ```
   log4j.logger.ros=DEBUG
   log4j.logger.roscpp=INFO
   ```
3. Add a reference to that file in the `.bashrc`
   ```
   export ROSCONSOLE_CONFIG_FILE=~/.rosconsole
   ```
4. Read the `.bashrc` or re-launch the shell
   ```
   $ source ~/.bashrc
   ```
The default setting is defined in the following file.
```
$ /opt/ros/melodic/share/ros/config/rosconsol.config
```

If you don't want to set DEBUG-mode permanently, you can comment out `export ROSCONSOLE_CONFIG_FILE=~/.rosconsole` in `.bashrc` and just run the following command.
```
$ export ROSCONSOLE_CONFIG_FILE=~/.rosconsole
```

(reference)
- http://dav.ee/blog/notes/archives/898

## How to see ROS_DEBUG (from GUIs)

- ros_logger_level
- rqt_console