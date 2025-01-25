Robot_Localization
==================

This warehouse is used to integrate nine-axis IMU and wheel ohmmeter data in ros2 humble, the parameters of which I adjusted by myself after many experiments.

## Requirement
You'll first need a wheeled odometer (odom1) and a nine-axis IMU from either Magic Technologies or Alpriz Energy. The driver code is wrong in Humble, but I've corrected it in my other warehouses, and it's called imu/data_raw.

## HOW TO BUILD
```bash
$ colcon build
```
## HOW TO USE
### STEP1：START YOUR ODOM1
```bash
$ . install/setup.bash
$ ros2 run micro_ros_agent micro_ros_agent udp4 --port 8888 -v6
```
### OR
```bash
$ . install/setup.bash
$ ros2 run micro_ros_agent micro_ros_agent serial -b 115200 --dev /dev/ttyACM0 -v6
```
### STEP2：START YOUR IMU
```bash
$ . install/setup.bash
$ ros2 launch gnss_imu_sim imu_driver_launch.py
```
### STEP3：START LOCALIZATION
```bash
$ . install/setup.bash
$ ros2 launch robot_localization ekf.launch.py
```
