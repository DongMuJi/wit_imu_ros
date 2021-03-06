# wit_imu_ros

ROS package for WIT inclinometer devices (https://wiki.wit-motion.com/english/doku.php)

## Supported devices
- WIT905

## How to compile
- It is assumed that catkin workspace is available already.
  - cd <your_path>/catkin_ws/src
  - clone this respository
  - cd ..
  - catkin_make
  - source devel/setup.bash

## How to launch
There are 3 options to launch the package.
1) Launch without IMU madgwick filter, magnetic data fusion and IMU transformer
  - roslaunch wit_imu_ros wit905_imu.launch
  
2) Launch with IMU madgwick filter, magnetic data fusion and IMU transformer
  - roslaunch wit_imu_ros wit905_filter.launch
  
  Please note ros-melodic-imu-filter-madgwick, ros-melodic-imu-transformer packages to be installed.

3) Launch with IMU madgwick filter, magnetic data fusion and IMU transformer and visualize through Rviz
  - roslaunch wit_imu_ros wit905_imu_test.launch
  
  Please note ros-melodic-imu-tools and other package mentioned in filter launch to be installed.

## Message Type

### ImuRaw

> Header header
>
> geometry_msgs/Vector3 acc
>
> geometry_msgs/Vector3 gyro
>
> geometry_msgs/Vector3 rpy
>
> geometry_msgs/Vector3 mag
>
> float64   temperature
  
## Published topics
- /wit/imu_data         (sensor_msgs/Imu Message)
- /wit/mag_data         (sensor_msgs/MagneticField)
- /wit/temparture_data  (sensor_msgs/Temperature)
- /wit/imu_raw_data     (wit_imu_ros/ImuRaw)
