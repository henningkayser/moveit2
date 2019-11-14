<img src="http://moveit.ros.org/assets/images/moveit2_logo_black.png" alt="MoveIt! Logo" width="200"/>

The MoveIt Motion Planning Framework for ROS 2

We are currently working on the upcoming Beta version of MoveIt 2.
More information about our roadmap and future milestones will be added soon.

### Build from Source

> Note: Currently, only the moveit\_core packages are being compiled.

These instructions assume you are running on Ubuntu 18.04.

1. [Install ROS2 Dashing](https://index.ros.org/doc/ros2/Installation/Linux-Install-Debians/) (Make sure to set `export CHOOSE_ROS_DISTRO=Dashing` and to source `/opt/ros/dashing/setup.bash`)

1. [Install ROS2 Build Tools](https://index.ros.org/doc/ros2/Installation/Linux-Development-Setup/#install-development-tools-and-ros-tools)

1. Create a colcon workspace:

        export COLCON_WS=~/ws_ros2/
        mkdir -p $COLCON_WS/src
        cd $COLCON_WS/src

1. Download the repository and install any dependencies:

        git clone git@github.com:ros-planning/moveit2.git
        vcs import < moveit2/moveit2.repos
        rosdep install -r --from-paths . --ignore-src --rosdistro Dashing -y

1. Configure and build the workspace:

        cd $COLCON_WS
        colcon build --merge-install --event-handlers desktop_notification- status-

1. Source the workspace:

        source $COLCON_WS/install/local_setup.bash


## Roadmap
The MoveIt Motion Planning Framework **for ROS 2.0**

- [Milestones](#milestones)
- [Overview of MoveIt!](http://moveit.ros.org)
- [Installation Instructions](http://moveit.ros.org/install/)
- [Documentation](http://moveit.ros.org/documentation/)
- [Get Involved](http://moveit.ros.org/documentation/contributing/)


## Continuous Integration Status

[![Build Status](https://travis-ci.org/ros-planning/moveit2.svg?branch=master)](https://travis-ci.org/ros-planning/moveit2)

## Docker Containers

TODO [Create ROS2 Docker containers for MoveIt!](https://github.com/ros-planning/moveit2/issues/15)

## ROS Buildfarm

Debian releases of MoveIt2 will not be available during the alpha development stage. Check back May 2019.
