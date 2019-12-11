# Debugging of rviz visualization of marker

## Overview

When you use video drivers except for nvidia driver, the markers (XX_list type) are not displayed in rviz correctly.

(ref)
- https://answers.ros.org/question/336462/ros-melodic-rviz-visualization-markers-bug/
- https://answers.ros.org/question/337916/rviz-points-color-bug-or-doing-something-wrong/

## Details

It is necessary to install some GPU drivers for OpenGL, which is used in rviz.

This page summarizes what to do in well-coordinated way.

- https://github.com/VCDP/KBL-G/wiki/KBL-G-AMD-VEGA-Driver-Getting-Started-Guide

1. **Install AMD GPU driver**

```
sudo apt install -y mesa-utils
```
`meta-utils` contains OpenGL tools (gixinfo, glxgears, glxdemo, glxheads).
It is unnecessary to install `mesa-utils-extra` or `vulkan-utils`. These two caused errors in my environment.

2. **Install AMD GPU driver package**
