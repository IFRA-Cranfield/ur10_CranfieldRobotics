# IFRA-Cranfield: ur10_CranfieldRobotics

## UR10 Robot Simulation and Control using ROS 2: Practical Examples

### Gazebo Simulation

This environment does not have any particular use/application, but simply visualizing the UR10 robot and it's end-effectors and stand in the Simulation Environment. Execute the following command to launch a ROS 2-Gazebo Simulation Environment of the UR10-Cranfield Robot:

```sh
# UR10 Robot alone on Cranfield University (IA Lab) Table:
ros2 launch ros2srrc_launch simulation.launch.py package:=ur10cranfield config:=ur10cranfield_1
```

### Gazebo Simulation + MoveIt!2-based Robot Control

Execute the following command to launch the ROS 2-Gazebo Simulation Environment along with the MoveIt!2 Framework, enabling the robot to be controlled, monitored, and operated through MoveIt!2. It also loads RVIZ for visualization and gives access to the custom ROS 2 tools (/Move, /RobMove, /RobPose) for robot manipulation and monitoring.

```sh
# UR10 Robot alone on Cranfield University (IA Lab) Table:
ros2 launch ros2srrc_launch moveit2.launch.py package:=ur10cranfield config:=ur10cranfield_1
```

Once the environment has been launched, there are few operations that can be done to interact with the robot. For more information, please have a look at this [link](https://github.com/IFRA-Cranfield/ros2_SimRealRobotControl/blob/humble/instructions/RobotOperation.md).

- Robot Movement: 

    ```sh
    # MoveJ:
    ros2 action send_goal -f /Move ros2srrc_data/action/Move "{action: 'MoveJ', movej: {joint1: 0.00, joint2: 0.00, joint3: 0.00, joint4: 0.00, joint5: 0.00, joint6: 0.00}, speed: 1.0}"
    # MoveL:
    ros2 action send_goal -f /Move ros2srrc_data/action/Move "{action: 'MoveL', movel: {x: 0.00, y: 0.00, z: 0.00}, speed: 1.0}"
    # MOveR:
    ros2 action send_goal -f /Move ros2srrc_data/action/Move "{action: 'MoveR', mover: {joint: '--', value: 0.00}, speed: 1.0}"
    # MoveROT:
    ros2 action send_goal -f /Move ros2srrc_data/action/Move "{action: 'MoveROT', moverot: {yaw: 0.00, pitch: 0.00, roll: 0.00}, speed: 1.0}"
    # MoveRP:
    ros2 action send_goal -f /Move ros2srrc_data/action/Move "{action: 'MoveRP', moverp: {x: 0.00, y: 0.00, z: 0.00, yaw: 0.00, pitch: 0.00, roll: 0.00}, speed: 1.0}"
    # MoveG (for the gripper):
    ros2 action send_goal -f /Move ros2srrc_data/action/Move "{action: 'MoveG', moveg: 0.0, speed: 1.0}"

    # RobMove:
    ros2 action send_goal -f /Robmove ros2srrc_data/action/Robmove "{type: '---', speed: 1.0, x: 0.0, y: 0.0, z: 0.0, qx: 0.0, qy: 0.0, qz: 0.0, qw: 0.0}"
    ```

- Monitor the state of the robot:

    ```sh
    # To check the state of the joints:
    ros2 run ros2srrc_execution RobotState.py
    ros 2 topic echo /joint_states

    # To check the end-effector pose:
    ros2 topic echo /Robpose
    ```

- Execute a Robot Program: The programs for the UR10-Cranfield Robot are stored inside the ur10cranfield ROS 2 Package, /programs folder. The following command is used to execute the programs (for more information, access this [link](https://github.com/IFRA-Cranfield/ros2_SimRealRobotControl/blob/humble/instructions/ProgramExecution.md)):

    ```sh
    # Example for the ur10_demo.yaml program:
    ros2 run ros2srrc_execution ExecuteProgram.py package:=ur10cranfield program:=ur10_demo
    ```

### MoveIt!2-based Control of the Real Robot

For more detailed instructions on how properly set-up any UR Robot for ROS 2 and to connect to the UR10 robot, please visit this [link-TBD]. Once that is ready, you can execute the following command to launch the UR's ROS 2 driver along with MoveIt!2, and our custom ROS 2 tools for robot operation:

```sh
# In this set-up, we consider:
#   - Ubuntu PC's IP Address is -> 192.168.1.2, manually set in the PC.
#   - UR10's IP Address is -> 192.168.1.10, manually set in the teach pendant.

# UR10 Robot alone on Cranfield University (IA Lab) Table:
ros2 launch ros2srrc_launch bringup_ur.launch.py package:=ur10cranfield config:=ur10cranfield_1 robot_ip:=192.168.1.10
```

- Robot Operation ROS 2 Nodes are available as for simulation.

- Robot State Monitoring ROS 2 Nodes are available as for simulation.

- Robot Programs can be executed as for simulation:

    ```sh
    # Example for the ur10_demo.yaml program:
    ros2 run ros2srrc_execution ExecuteProgram.py package:=ur10cranfield program:=ur10_demo
    ```