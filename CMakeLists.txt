cmake_minimum_required(VERSION 3.8)
project(asv_arov_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
rosidl_generate_interfaces(${PROJECT_NAME}
  "srv/SetRecording.srv"
  "srv/PositionTargetLocalNED.srv"
  "srv/SetMAVMode.srv"
  "srv/SetArmDisarm.srv"
  "srv/GetOdom.srv"
  "srv/SetPump.srv"
  "srv/SetCenterCamera.srv"
  "srv/ControlMode.srv"
  "action/NavigateAprilTags.action"
  "action/NavigationAction.action"
  "action/GoToDepth.action"
  "action/GoToSide.action"
  "action/AROVCommandAction.action"
  "action/DumbCleanAction.action"
  DEPENDENCIES builtin_interfaces geometry_msgs std_msgs nav_msgs
 )
ament_export_dependencies(rosidl_default_runtime)

ament_package()