cmake_minimum_required(VERSION 3.10.2)
project(uvone_teleop)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  geometry_msgs
  ds4_driver
  uvone_msgs
  sensor_door_msgs
  std_srvs
)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS})

add_executable(teleop_ds4 src/teleop_ds4.cpp)
target_link_libraries(teleop_ds4 ${catkin_LIBRARIES})
add_dependencies(teleop_ds4 ${catkin_EXPORTED_TARGETS})

install(PROGRAMS
  scripts/turtlebot_teleop_key
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
install(TARGETS teleop_ds4
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
