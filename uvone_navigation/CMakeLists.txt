cmake_minimum_required(VERSION 3.0.2)
project(uvone_navigation)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED 
  roscpp
  rospy
  std_msgs
  actionlib
  uvone_msgs
  sensor_door_msgs
  roslib
)
catkin_package(
  CATKIN_DEPENDS roscpp rospy std_msgs actionlib uvone_msgs sensor_door_msgs roslib
)

include_directories(${catkin_INCLUDE_DIRS})

add_executable(simple_navigation_goals src/test.cpp)
target_link_libraries(simple_navigation_goals ${catkin_LIBRARIES})

add_executable(command_sender src/command_sender.cpp)
target_link_libraries(command_sender ${catkin_LIBRARIES})

add_executable(command_writer src/command_writer.cpp)
target_link_libraries(command_writer ${catkin_LIBRARIES})

catkin_install_python(PROGRAMS scripts/create_trace.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(TARGETS command_writer command_sender simple_navigation_goals
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
