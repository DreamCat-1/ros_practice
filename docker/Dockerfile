FROM nvidia/cuda:12.3.2-cudnn9-devel-ubuntu20.04

# Set environment variable to avoid interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    lsb-release \
    gnupg2 \
    curl \
    && rm -rf /var/lib/apt/lists/*

RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

RUN curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add -

RUN apt-get update && apt-get install -y \
    ros-noetic-desktop-full \
    vim \
    git \
    nano \
    wget \
    python3-rosdep \ 
    python3-rosinstall \
    python3-rosinstall-generator \
    python3-wstool \
    build-essential \
    python3-rosdep \
    cmake build-essential unzip pkg-config autoconf \
    libboost-all-dev \
    libvtk7-dev libgtk-3-dev libatlas-base-dev gfortran \
    libparmetis-dev \
    python3-wstool python3-catkin-tools \
    python3-pcl \
    pcl-tools \
    libpcl-dev \
    opencl-headers \
    ocl-icd-libopencl1 \
    ocl-icd-opencl-dev \
    libnvidia-compute-575 \
    tmux \
    python3-empy \

    && rm -rf /var/lib/apt/lists/* #  Delete the temporary package lists and remove unnecessary files

# RUN sudo rosdep update && sudo rosdep init
RUN rosdep init && rosdep update

RUN echo "source /opt/ros/noetic/setup.bash" >> /root/.bashrc

RUN echo "source ~/.bashrc"

WORKDIR /root/catkin_ws

# Clean up
# RUN rm -rf /var/lib/apt/lists/*
EXPOSE 8888
# -c read and execute the command string provided as its argument
# CMD ["/bin/bash", "-c", "source /root/.bashrc && /bin/bash"] 
CMD ["/bin/bash"]
