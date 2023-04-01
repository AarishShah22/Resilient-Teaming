# Resilient Teaming Project

This is the repository for the Resilient Teaming project with the Barton Research Group at the University of Michigan.

Follow the below steps:

Create a Catkin workspace:

    $ mkdir -p catkin_ws/src
    $ catkin_make

Follow the installation instructions at the two links: [ROS Driver](https://github.com/AarishShah22/resilient-teaming-ros-driver) and [ZED ROS Wrapper](https://github.com/AarishShah22/resilient-teaming-zed-ros-wrapper) in the src folder. Then source the workspace.

    $ cd ~/catkin_ws
    $ source devel/setup.bash

To make the robot move, follow the instructions at the [ROS Driver](https://github.com/AarishShah22/resilient-teaming-ros-driver) repository. 

To get the odometry information of the robot, follow the above commands to get the ROS Driver and ZED ROS Wrapper packages first. Then, use the instructions in the ROS Driver repository to get the robot moving. You should have a "driver.launch" in one terminal and "controller_node" in a second terminal. Then, in yet another terminal, use the following command:

    $ roslaunch roboteq_motor_controller_driver diff_odom.launch

The odometry node takes orientation information from the IMU attached to the ZED camera, and combines it with distance information extracted from wheel encoders to give final odometry. This is because the wheel odometry works well in the case of straight line motion, but does not account for rotations accurately. Thus, we use the IMU for figuring out the robot's heading.
