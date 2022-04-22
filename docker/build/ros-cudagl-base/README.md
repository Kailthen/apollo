
### Create image
```bash
# ros1
export ROS_TAG=noetic-desktop-full
export CUDAGL_TAG=11.4.1-devel-ubuntu20.04
docker build -t evas/ai:${ROS_TAG}_cuda${CUDAGL_TAG} -f ./Dockerfile --build-arg ROS_TAG=${ROS_TAG} --build-arg CUDAGL_TAG=${CUDAGL_TAG} .

# ros2
export ROS_TAG=galactic-desktop
export CUDAGL_TAG=11.4.1-devel-ubuntu20.04
docker build -t evas/ai:${ROS_TAG}_cuda${CUDAGL_TAG} -f ./Dockerfile --build-arg ROS_TAG=${ROS_TAG} --build-arg CUDAGL_TAG=${CUDAGL_TAG} .
```

```
cd docker/build
bash build_docker.sh -m build -g cn -d stable -t 20220413_1300 -f cyber.x86_64.dockerfile
```

=====.=====.===== Docker Build Preview for cyber =====.=====.=====
|  Generated image: apolloauto/apollo:cyber-x86_64-20.04-20220413_1300
|  FROM image: ros_cudagl:galactic-desktop_cuda11.4.1-devel-ubuntu20.04
|  Dockerfile: cyber.x86_64.dockerfile
|  TARGET_ARCH=x86_64, HOST_ARCH=x86_64
|  INSTALL_MODE=build, GEOLOC=cn, APOLLO_DIST=stable
=====.=====.=====.=====.=====.=====.=====.=====.=====.==

```
apolloauto/apollo:cyber-x86_64-20.04-20220413_1300

bash build_docker.sh -m build -g cn -d stable -t 20220413_1300 -f dev.x86_64.dockerfile 


```
=====.=====.===== Docker Build Preview for dev =====.=====.=====
|  Generated image: apolloauto/apollo:dev-x86_64-20.04-20220413_1335
|  FROM image: apolloauto/apollo:cyber-x86_64-20.04-20220413_1300
|  Dockerfile: dev.x86_64.dockerfile
|  TARGET_ARCH=x86_64, HOST_ARCH=x86_64
|  INSTALL_MODE=build, GEOLOC=cn, APOLLO_DIST=stable
=====.=====.=====.=====.=====.=====.=====.=====.=====.=====.=====.=====.=====
