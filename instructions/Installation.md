# IFRA-Cranfield: ur10_CranfieldRobotics

## Installation Steps

The steps below must be followed in order to properly set up a ROS 2 Jazzy machine which is needed for the usage of the ROS 2 packages in the ur10_CranfieldRobotics repository. It is recommended to install Ubuntu 24.04 Desktop on your PC for optimal performance, but a VM could be used for simple simulations and executions.

__REQUIRED: Install the ros2_SimRealRobotControl GitHub repository__

The ROS 2 packages developed in UR10-CranfieldRobotics are based on IFRA-Cranfield's [ros2_SimRealRobotControl](https://github.com/IFRA-Cranfield/ros2_SimRealRobotControl/tree/jazzy) GitHub repository. Therefore, ros2_SimRealRobotControl must be installed in order to set up UR10-CR in any Ubuntu 24.04 + ROS 2 Jazzy machine.

Installation steps can be found at: https://github.com/IFRA-Cranfield/ros2_SimRealRobotControl/blob/jazzy/instructions/Installation.md

__Download and install ur10_CranfieldRobotics__

```sh
cd ~/dev_ws/src
git clone -b jazzy https://github.com/IFRA-Cranfield/ur10_CranfieldRobotics
cd ~/dev_ws
colcon build
```
