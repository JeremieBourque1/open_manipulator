# open_manipulator
Fork of the Robotis open_manipulator 4-dof robot arm

## Dependencies
Use this command to install all dependencies:
`rosdep install --from-paths src --ignore-src -r -y`
## How to use
1. `roslaunch open_manipulator_moveit_config demo_gazebo.launch`
2. In RViz, wait for the interactive markers to appear then drag the end effector to the desired goal pose
3. Click on the `Plan & Execute` button in the `Planning` tab of the `MotionPlanning` panel.
4. You should see the robot move to the desired pose in RViz and in Gazebo.
