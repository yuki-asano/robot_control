# References
- github
  - https://github.com/ROBOTIS-GIT/open_manipulator
- e-Manual
  - https://emanual.robotis.com/docs/en/platform/openmanipulator_x/overview/      

# Install

```
cd ~/catkin_ws/src
wstool merge -t . robot_control/robots/open_manipulator_x/install/open_manipulator_x.rosinstall
wstool update

rosdep install -y -r --from-paths . --ignore-src # execute on src dir
catkin build
```

### for kinetic devel  
In kinetic devel, open_manipulator.urdf.xacro is existing, but open_manipulator_robot.urdf.xacro is not.
  
```
roscd open_manipulator_description/urdf
cp open_manipulator.urdf.xacro open_manipulator_robot.urdf.xacro
```

# Connection
- connect OpenMANIPULATOR-x to OpenCR board via a TTL port
  - https://emanual.robotis.com/docs/en/parts/controller/opencr10/

# Sample
- controller
```
[terminal1]
roslaunch open_manipulator_controllers joint_trajectory_controller.launch sim:=false usb_port:=/dev/ttyACM0 
```

- motion planning
```
[terminal2]
./open_manipulator_x_sample.py
```

or Rviz gui
1. move end-effector on Rviz
2. click 'Plan & Execute' button