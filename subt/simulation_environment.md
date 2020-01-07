# Simulation Settings

## 2019/01/07

- localizer_lamp
    - commit hash: 52a98403025cc79a213eaa891d6936ecddd6a7fc
    - branch: feature/uwb_loop_suggest
- localizer_lo_frontend
    - commit hash: 4b218c9bcb2f5f02a55ff390249e7ff44c9972bc
    - branch: release/2.3-dec-milestone
    - others:
        - `<arg name="b_use_two_pc" default="false"/>`
- localizer_uwb_frontend
    - commit hash: dd2ae5ee622e9c5d8ad01d3a3822b2e18f536b47
    - branch: feature/loop_closure_suggest
- comm_node_manager
    - commit hash: 87a0e1df1c79510fd234dc23c1bef3d2c9d157ad
    - branch: feature/uwb_testing
- core_messages
    - commit hash: 4423b620582e407f1b2d7adddcde13cce35f94d3
    - branch: release/2.3-dec-milestone

```
<!--<remap from="~lio_odom" to="lo_frontend/odometry"/> -->
+      <remap from="~lio_odom" to="lo_frontend/odometry"/>

<!--<remap from="~lio_odom" to="lo_frontend/odometry"/> -->
+      <remap from="~lio_odom" to="lo_frontend/odometry"/>

session_name: husky_refactor

# before_script: "~/sim_/scripts/cleanup.sh"

# Default environment variables; Overwrite from command line
environment:
  # LOG_PATH: /home/costar/data/EagleMineStandard
  # LOG_PATH: /home/nobuhiro/data/parking_oct28/husky3_2019-10-28-20-43-00_parking_t3_lamp/rosbag
  # LOG_PATH: /home/nobuhiro/data/parking_oct28/husky3_2019-10-28-20-18-00_parking_t2_lamp/rosbag
  # LOG_PATH: /home/nobuhiro/data/husky3_2019-11-21-22-43-00_301_baseline_test10/rosbag
  # LOG_PATH: /home/nobuhiro/data/husky2_2019-07-29-23-53-00_test/rosbag
  # LOG_PATH: /home/nobuhiro/data/parking_nov15/husky2_2019-11-15-22-36-00_uwb_comm_flower/rosbag
  # LOG_PATH: /home/nobuhiro/data/2019-12-19-JPL301_game_playing/husky2_2019-12-19-22-00-00_b301_t2_game/rosbag
  # LOG_PATH: /home/nobuhiro/data/2019-12-16_husky3_JPL82_uwb/husky3_2019-12-16-22-06-00_uwb_test11/rosbag
  # LOG_PATH: /home/nobuhiro/data/husky3_2019-12-23-16-40-00_b198_t2_data-collection/rosbag
  LOG_PATH: /home/nobuhiro/data/husky2_2019-12-23-15-58-00_b198_t1_game/rosbag
  # LOG_PATH: /home/nobuhiro/data/husky3_2019-12-23-17-17-00_b198_t3_data-collection/rosbag
  # LOG_PATH: /home/nobuhiro/data/parking_nov15/husky2_2019-11-15-22-15-00_uwb_comm_C/rosbag
  # LOG_PATH: /media/nobuhiro/UBUNTU 16_0/imu_test/rosbag
  ROBOT_NAME: husky2
  BASE_NAME: base1

options:
  default-command: /bin/bash

windows:
- window_name: lamp
  focus: true
  layout: tiled
  panes:
    - roscore
    - sleep 4; rosparam set /use_sim_time true; roslaunch lamp turn_on_lamp.launch robot_namespace:=$ROBOT_NAME
    - sleep 6; rosparam set /use_sim_time true; roslaunch lamp turn_on_robot_viz.launch robot_namespace:=$ROBOT_NAME
    - sleep 2; rosparam set /use_sim_time true; roslaunch lamp turn_on_lamp_base.launch robot_namespace:=$BASE_NAME
    - sleep 3; rosparam set /use_sim_time true; roslaunch uwb_frontend uwb_frontend.launch robot_namespace:=$ROBOT_NAME
    - sleep 5; rosparam set /use_sim_time true; roslaunch lamp turn_on_lamp_pgo.launch robot_namespace:=$ROBOT_NAME
    - sleep 5; rosparam set /use_sim_time true; roslaunch lamp turn_on_lamp_loop_closure.launch robot_namespace:=$ROBOT_NAME
    - sleep 3; rosparam set /use_sim_time true; roslaunch comm_node_manager comm_node_manager.launch robot_namespace:=$ROBOT_NAME
    # - sleep 5; rosbag play -l -r1.0 -s90 $LOG_PATH/*.bag --prefix=/$ROBOT_NAME --clock
    # - sleep 5; rosbag play -l -r 1.0 -s 0 $LOG_PATH/husky3_lidar* $LOG_PATH/husky3_comms_2* $LOG_PATH/husky3_state* --clock
    - sleep 5; rosbag play -l -r 1.0 -s 0 $LOG_PATH/husky2_lidar* $LOG_PATH/husky2_comms_2* $LOG_PATH/husky2_state* --clock
    # - sleep 5; rosbag play -l -r 1.0 -s 0 $LOG_PATH/husky2_lidar* $LOG_PATH/husky2_comms_2* $LOG_PATH/husky2_state* /home/nobuhiro/temp/comm_node_status_flower.bag --clock
    # - sleep 5; rosbag play -l -r 1.0 -s 0 $LOG_PATH/husky2_lidar* $LOG_PATH/husky2_comms_2* $LOG_PATH/husky2_tf_* --clock
    # - sleep 5; rosbag play -l -r 1.0 -s 0 $LOG_PATH/* --clock
    # - sleep 5; rosbag play -l -r 1.0 -s 80 $LOG_PATH/husky3_lidar* $LOG_PATH/husky3_comms_2* --clock
    # - sleep 5; rosbag play -l -r 1.0 -s 0 $LOG_PATH/*.bag --clock
    # - sleep 5; rosbag play -r1.0 -s0 $LOG_PATH/*.bag --clock
    - sleep 5; rosparam set /use_sim_time true; roslaunch lo_frontend lo_frontend.launch robot_namespace:=$ROBOT_NAME
    - sleep 1; rosparam set /use_sim_time true; rosrun tf2_ros static_transform_publisher 0 0 0 0 0 0 /$ROBOT_NAME/velodyne /$ROBOT_NAME/base_link # only for Eagle mine
    # - sleep 1; rosparam set /use_sim_time true; rosrun tf2_ros static_transform_publisher 0 0 0 0 0 0 /$ROBOT_NAME/velodyne_front /$ROBOT_NAME/base_link # only for Eagle mine
    - sleep 1; rosparam set /use_sim_time true; rosrun tf2_ros static_transform_publisher 0 0 0 0 0 0 /world /$ROBOT_NAME/map # only for Eagle mine
    - sleep 1; rosparam set /use_sim_time true; rosrun tf2_ros static_transform_publisher 0 0 0 0 0 0 /world /$BASE_NAME/map # base station
    - sleep 2; rosparam set /use_sim_time true; rosrun rviz rviz -d ~/.rviz/lamp_husky2.rviz
    # - sleep 2; rosparam set /use_sim_time true; rosrun rviz rviz -d ~/.rviz/lamp_base.rviz
```