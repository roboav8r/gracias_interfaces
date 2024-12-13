cmake_minimum_required(VERSION 3.8)
project(situated_hri_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(audio_common_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(diagnostic_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Auth.msg"
  "msg/CategoricalDistribution.msg"
  "msg/Comm.msg"
  "msg/Comms.msg"
  "msg/HierarchicalCommand.msg"
  "msg/HierarchicalCommands.msg"
  "msg/Identity.msg"
  "srv/ObjectVisRec.srv"
  "srv/GestureRec.srv"
  "srv/SceneAudioRec.srv"
  "srv/SceneVisRec.srv"
  "srv/RecordEpoch.srv"
  DEPENDENCIES geometry_msgs sensor_msgs audio_common_msgs diagnostic_msgs
 )

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
