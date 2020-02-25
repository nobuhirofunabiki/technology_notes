# Hardware Test Tips (for SubT)
Last update: 2019/11/15

## Hardware setup
- Things
  - pc for the base station
  - SILVUS communication hub for the base station
- communication between Huksy and the base station

## Update the software cords
- vcs pull
- vcs check (gc: alias)

## tmux
- How to make the pane large?
- ctrl b + ctrl n
- ctrl b + ctrl x

## Activation of robots and a base station
- connect to the robot
  - `ssh husky1`
- launch the robots and the base station
  - `launch-husky`
  - `launch base`

- husky
- husky-artifact

- timeout 5 rosrun tmux_scripts cleanup.sh

Before running, we should do the fiducial caribration

On the base station,
- export ROBOT_NAME=husky3 && export OPS_ENV=jpl && launch-fc
- Just run the fiducial calibration node on the robot

Following things should be activated before running
1. FiducialCalibrationFromFile
2. Localizer
3. ArtifactService

Should do logging just before starting a mission
Should check Localizer /husky3/resillency_logic

## Other tips

- git
  - `git commit --amend --author="Nobuhiro Funabiki <nobuhiro.funabiki@jpl.nasa.gov>"`
- ssd
  - `sudo mount /dev/sdb1 /mnt/ssd`
  - `sudo umount /mnt/ssd`

```
$ ROS_MASTER_URI=http://husky2:11311 rviz -d $(rospack find rviz_config)/cfg/ops.rviz
```