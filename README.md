# IDP Data Collector

This package lets you collect the autonomous/connected car sensor data with ROS.

## Environment

- Ubuntu 18.04
- GPU: RTX 2060 Super / GTX 1650 Ti

## Prerequisite

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
$ catkin_make -DCMAKE_BUILD_TYPE=Release
$ source devel/setup.bash
```

## Usage
```
$ rosbag record /tf_static /ublox_gps/fix /ublox_gps/navpvt /ublox_gps/navsat /ublox_gps/fix_velocity /ublox_gps/navstatus /zed2/zed_node/imu/data /zed2/zed_node/left/camera_info /zed2/zed_node/left/image_rect_color /zed2/zed_node/left_cam_imu_transform /zed2/zed_node/point_cloud/cloud_registered /zed2/zed_node/pose /zed2/zed_node/right/camera_info /zed2/zed_node/right/image_rect_color /zed2/zed_node/stereo/image_rect_color
```

## Files

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

### ublox gps
```
$ roslaunch ublox_gps ublox_device.launch node_name:=ublox_gps param_file_name:=neo_m8p_rover
```
