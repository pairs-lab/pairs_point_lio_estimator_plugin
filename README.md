# pairs_point_lio_estimator_plugin

Pluginlib plugin that wraps Point-LIO LiDAR-inertial odometry as a state
estimator for the PAIRS UAV stack. The estimation manager (`pairs_uav_managers`)
loads it like any other `StateEstimator`, so Point-LIO odometry can feed the
UAV's state estimate and be switched in alongside the other estimators in the
stack.

## Contents
- `point_lio/PointLioEstimatorPlugin` — a `pairs_uav_managers::StateEstimator` plugin backed by Point-LIO.

## Branches
- `ros1` — ROS 1 Noetic (catkin)
- `ros2` — ROS 2 Jazzy (ament_cmake)

## Install (ROS 1 Noetic)
```bash
sudo apt install ros-noetic-pairs-point-lio-estimator-plugin
```

## License
BSD 3-Clause. Derived from the CTU-MRS `pairs_point_lio_estimator_plugin` package; the original
copyright is retained in [LICENSE](LICENSE).
