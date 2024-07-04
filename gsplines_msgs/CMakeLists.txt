cmake_minimum_required(VERSION 3.8)
project(gsplines_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(control_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(MSG_files "msg/Basis.msg" "msg/GSpline.msg" "msg/JointGSpline.msg")

set(SRV_files "srv/GetBasis.srv" "srv/GSplineTrigger.srv"
              "srv/JointGSplineTrigger.srv")

set(ACTION_files "action/FollowJointGSpline.action")

rosidl_generate_interfaces(
  ${PROJECT_NAME}
  ${MSG_files}
  ${SRV_files}
  ${ACTION_files}
  DEPENDENCIES
  action_msgs
  builtin_interfaces
  std_msgs
  trajectory_msgs
  control_msgs)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
