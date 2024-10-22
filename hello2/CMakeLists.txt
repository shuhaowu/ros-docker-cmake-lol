cmake_minimum_required(VERSION 3.8)
project(hello2)

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_executable(talker src/main.cpp)
ament_target_dependencies(talker rclcpp std_msgs)

install(
  TARGETS talker
  EXPORT talker_exe
  DESTINATION lib/${PROJECT_NAME}
)

ament_export_targets(talker_exe)

ament_package()
