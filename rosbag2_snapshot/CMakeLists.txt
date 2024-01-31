cmake_minimum_required(VERSION 3.5)
project(rosbag2_snapshot)

find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

ament_auto_add_library(${PROJECT_NAME} SHARED
  include/rosbag2_snapshot/snapshotter.hpp
  include/rosbag2_snapshot/qos.hpp
  src/qos.cpp
  src/snapshotter.cpp
)

rclcpp_components_register_node(${PROJECT_NAME}
  EXECUTABLE snapshotter
  PLUGIN rosbag2_snapshot::Snapshotter
)

rclcpp_components_register_node(${PROJECT_NAME}
  EXECUTABLE snapshotter_client
  PLUGIN rosbag2_snapshot::SnapshotterClient
)

ament_auto_package()
