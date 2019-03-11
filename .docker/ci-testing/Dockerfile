# moveit/moveit2:crystal-ci-testing
# Sets up a base image to use for running Continuous Integration on Travis

FROM moveit/moveit2:crystal-ci
MAINTAINER Dave Coleman dave@picknik.ai

# Switch to ros-shadow-fixed
RUN echo "deb http://packages.ros.org/ros2-testing/ubuntu `lsb_release -cs` main" | tee /etc/apt/sources.list.d/ros2-latest.list

# Upgrade packages to ros-shadow-fixed and clean apt-cache within one RUN command
RUN apt-get -qq update && \
    apt-get -qq dist-upgrade && \
    #
    # Clear apt-cache to reduce image size
    rm -rf /var/lib/apt/lists/*
