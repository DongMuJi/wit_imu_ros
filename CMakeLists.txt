cmake_minimum_required(VERSION 3.0.2)
project(wit_imu_ros)

find_package(catkin REQUIRED COMPONENTS
  nav_msgs
  roscpp
  sensor_msgs
  std_msgs
  geometry_msgs
  tf2
  tf2_geometry_msgs
  serial
  message_generation
)

## Generate messages in the 'msg' folder
add_message_files(
 FILES
 ImuRaw.msg
)

## Generate added messages and services with any dependencies listed here
generate_messages(
 DEPENDENCIES
 std_msgs
 geometry_msgs
)


find_package(Boost REQUIRED COMPONENTS system)

catkin_package(CATKIN_DEPENDS nav_msgs roscpp sensor_msgs std_msgs geometry_msgs tf2 tf2_geometry_msgs message_runtime)

include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(${PROJECT_NAME}_node src/wit_imu_ros_node.cpp src/wit_imu_parser.cpp)

target_link_libraries(${PROJECT_NAME}_node ${catkin_LIBRARIES})

install(TARGETS ${PROJECT_NAME}_node RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})



