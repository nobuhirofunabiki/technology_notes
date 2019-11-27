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
- 

## Activation of robots and a base station
- connect to the robot
  - `ssh husky1`
- launch the robots and the base station
  - `launch-husky`
  - `launch base`

- husky
- husky-artifact


- timeout 5 rosrun tmux_scripts cleanup.sh

## Other tips

- git
  - `git commit --amend --author="Nobuhiro Funabiki <nobuhiro.funabiki@jpl.nasa.gov>"`
- ssd
  - `sudo mount /dev/sdb1 /mnt/ssd`
  - `sudo mount /mnt/ssd`