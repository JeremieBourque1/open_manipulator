# open_manipulator
Fork of the Robotis open_manipulator 4-dof robot arm with custom moveit configurations for real time servoing and motion planning in a Gazebo simulation.

## Dependencies
Use this command to install all dependencies:
`rosdep install --from-paths src --ignore-src -r -y`
## How to do real time servoing with moveit_servo 
1. `roslaunch open_manipulator_moveit_config demo_gazebo.launch`
2. By default, the right controller will be running so there is no need to switch controllers
3. Launch moveit_servo with `roslaunch open_manipulator_moveit_config moveit_servolaunch`
4. If you do not have a gamepad, you can send twist commands to the moveit_servo with the following comand:
    ```bash
    rostopic pub -r 100 -s /servo_server/delta_twist_cmds geometry_msgs/TwistStamped "header: auto
    twist:
    linear:
        x: 0.0
        y: 0.01
        z: -0.01
    angular:
        x: 0.0
        y: 0.0
        z: 0.0"
    ```
5. If instead you have a gamepad, you can use it to control the arm with `roslaunch open_manipulator_teleop gamepad_to_twist.launch `<br>
**Note:** make sure you are using the right input (jsX) in `gamepad_to_twist.launch`
6. You should now be able to control the arm in Gazebo.

## How to do motion planning
1. `roslaunch open_manipulator_moveit_config demo_gazebo.launch`
2. Switch to the arm controller with:
    ```bash
    rosservice call /controller_manager/switch_controller "start_controllers: ['arm_controller']
    stop_controllers: ['joint_group_position_controller']
    strictness: 0
    start_asap: false
    timeout: 0.0"
    ```
3. In RViz, wait for the interactive markers to appear and move the end effector to a goal position.
4. Click on the `Plan & Execute` button in the `Planning` tab of the `MotionPlanning` pannel.
5. You should see the robot move in RViz and Gazebo
