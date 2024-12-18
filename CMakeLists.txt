cmake_minimum_required(VERSION 3.5)
project(robot_interfaces)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find required dependencies
find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)

# Ensure that ament_cmake itself is exported


rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Line2Pts.msg"
  "msg/LineList.msg"
  "srv/PointTurn.srv"
  DEPENDENCIES builtin_interfaces std_msgs geometry_msgs
)
ament_export_dependencies(ament_cmake)
# ament_export_dependencies(rosidl_default_runtime)
# ament_export_include_directories(${PROJECT_NAME}/msg)

ament_package()
