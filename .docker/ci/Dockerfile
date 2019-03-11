# moveit/moveit2:crystal-ci
# Sets up a base image to use for running Continuous Integration on Travis

FROM ros:crystal-ros-base-bionic
MAINTAINER Dave Coleman dave@picknik.ai

ENV TERM xterm

# Setup overlay workspace
ENV OVERLAY_WS /root/ws_moveit
WORKDIR $OVERLAY_WS

# Commands are combined in single RUN statement with "apt/lists" folder removal to reduce image size
# https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#minimize-the-number-of-layers
RUN \
    # Update apt package list as previous containers clear the cache
    apt-get -qq update && \
    apt-get -qq dist-upgrade && \
    #
    # Install some base dependencies
    apt-get -qq install -y \
        # Some source builds require a package.xml be downloaded via wget from an external location
        wget \
        # Required for rosdep command
        sudo \
        # Preferred build tools
        python3-colcon-common-extensions \
        python3-vcstool \
        clang clang-format-3.9 clang-tidy clang-tools \
        ccache \
        # package dependencies (NOTE: will be installed with rosdep in the future)
        libboost-all-dev \
        libglew-dev \
        freeglut3-dev \
        pkg-config \
        libfcl-dev \
        libassimp-dev \
        libqhull-dev \
        ros-$ROS_DISTRO-action-msgs \
        ros-$ROS_DISTRO-resource-retriever \
        ros-$ROS_DISTRO-image-transport \
        python3-vcstool \
        libopencv-dev && \
    #
    # Create source directory
    mkdir src && \
    cd src && \
    #
    # Download moveit source, so that we can get necessary dependencies
    wget -q https://raw.githubusercontent.com/ros-planning/moveit2/master/moveit2.repos && \
    vcs import < moveit2.repos && \
    #
    # TODO: install packages with rosdep once crystal releases are available
    # Download all dependencies of MoveIt!
    #rosdep update && \
    #rosdep install -y --from-paths . --ignore-src --rosdistro ${ROS_DISTRO} --as-root=apt:false && \
    #
    # Remove the source code from this container
    # TODO: in the future we may want to keep this here for further optimization of later containers
    cd .. && \
    rm -rf src/ && \
    #
    # Clear apt-cache to reduce image size
    rm -rf /var/lib/apt/lists/*

# Continous Integration Setting
ENV IN_DOCKER 1
