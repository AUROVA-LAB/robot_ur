# robot_ur

...

```
source /opt/ros/melodic/setup.bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```

```
cd src
git clone https://github.com/AUROVA-LAB/robot_ur.git
cd ..
```

```
sudo apt update -qq
rosdep update
rosdep install --from-paths src --ignore-src -y
```

```
catkin_make
source devel/setup.bash
```

```
roslaunch ur5e_moveit_config demo.launch
```

```
roslaunch ur_calibration calibration_correction.launch robot_ip:=<robot_ip> target_filename:="${HOME}/my_robot_calibration.yaml"
roslaunch ur_robot_driver <robot_type>_bringup.launch robot_ip:=<robot_ip> kinematics_config:="${HOME}/my_robot_calibration.yaml"
roslaunch <robot_type>_moveit_config move_group.launch 
roslaunch <robot_type>_moveit_config moveit_rviz.launch rviz_config:=$(rospack find <robot_type>_moveit_config)/launch/moveit.rviz
```
