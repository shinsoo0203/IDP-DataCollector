# IDP Data Collector

This package lets you collect the autonomous/connected car sensor data with ROS.

## Prerequisites

- Ubuntu 18.04
- GPU: RTX 2060 Super / GTX 1650 Ti
- [CUDA 11.0](https://developer.nvidia.com/cuda-downloads)
- [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu)


## Sensor Specification

- AI stereo camera: ZED 2
- RTK-GPS: NEO-M8P-2 Board


## Build this repository
```
$ cd ~/src
$ git clone --recursive https://github.com/shinsoo0203/IDP-DataCollector.git
$ git submodule update --init --recursive
```

## Settings

- Add submodule on this repository
```
Fork the target github repository
$ cd ~/src
$ git submodule add [forked submodule git address]
```

#### usb camera

#### ZED2 Stereo Camera

- SDK install
```
$ cd /usr/local/zed
```

- Build the repository
```
$ cd ~/src
$ git clone --recursive https://github.com/shinsoo0203/zed-ros-wrapper.git
$ cd ../
$ rosdep install --from-paths src --ignore-src -r -y
$ catkin_make -DCMAKE_BUILD_TYPE=Relase
$ source ./devel/setup.bash
```

- Update the repository and re-build
```
$ git checkout master
$ git pull --recurse-submodules # update recursively all the submodules
$ roscd
$ cd ..
$ rm -rf build
$ rm -rf devel
$ catkin_make -DCMAKE_BUILD_TYPE=Release
```

- Run the ZED wrapper
```
$ roslaunch zed_wrapper zed2.launch
```
