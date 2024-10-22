cmake_minimum_required(VERSION 3.8)
project(docker_lol)

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(hello2 REQUIRED)

get_filename_component(INSTALL_DIR "${CMAKE_INSTALL_PREFIX}" DIRECTORY)
message(STATUS "ABC: ${INSTALL_DIR} ${CMAKE_CURRENT_BINARY_DIR}")

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/image
  DEPENDS hello2::talker
  COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/scripts/lol ${INSTALL_DIR} ${CMAKE_CURRENT_BINARY_DIR}/image my-crappy-image
)

add_custom_target(docker_image_lol
  ALL
  DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/image
)

ament_package()
