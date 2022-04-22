ARG ROS_TAG
ARG CUDAGL_TAG

# obtain ros image
FROM docker.io/osrf/ros:${ROS_TAG} AS ros

# base image off of cudagl
FROM docker.io/nvidia/cudagl:${CUDAGL_TAG}

# copy the entire ros image into the cudagl image
COPY --from=ros / /

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F60F4B3D7FA2AF80

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
  curl tmux unzip python3-catkin-tools \
  wget git vim \
  python3-software-properties \
  software-properties-common dirmngr apt-transport-https lsb-release ca-certificates

ARG CUDNN_VERSION=8.2.2.26-1+cuda11.4
ARG TENSORRT_VERSION=8.2.2-1+cuda11.4
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y install --no-install-recommends \
  libcudnn8-dev=$CUDNN_VERSION \
  libnvinfer8=$TENSORRT_VERSION \
  libnvinfer-dev=$TENSORRT_VERSION \
  libnvinfer-plugin8=$TENSORRT_VERSION \
  libnvinfer-plugin-dev=$TENSORRT_VERSION \
  libnvonnxparsers8=$TENSORRT_VERSION \
  libnvonnxparsers-dev=$TENSORRT_VERSION \
  libnvparsers8=$TENSORRT_VERSION \
  libnvparsers-dev=$TENSORRT_VERSION \
  libcudnn8=$CUDNN_VERSION

RUN sed -i "s@http://archive.ubuntu.com@http://repo.huaweicloud.com/@g" /etc/apt/sources.list

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y install --no-install-recommends \
  pcl-tools libpcl-* 

# RUN useradd -m work && echo "work:work" | chpasswd && adduser work sudo
# RUN echo "work ALL=(ALL) NOPASSWD : ALL" > /etc/sudoers.d/nopasswd4sudo 

# USER work
# WORKDIR /home/work

CMD /bin/bash