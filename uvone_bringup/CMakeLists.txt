cmake_minimum_required(VERSION 3.10.2)
project(uvone_bringup)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  kobuki_msgs
  roscpp
  uvone_msgs
  sensor_door_msgs
)

catkin_package(
  CATKIN_DEPENDS kobuki_msgs uvone_msgs sensor_door_msgs
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(light_node src/light_node.cpp)
target_link_libraries(light_node ${catkin_LIBRARIES})
add_dependencies(light_node ${catkin_EXPORTED_TARGETS})

add_executable(light_battery_node src/light_battery_node.cpp)
target_link_libraries(light_battery_node ${catkin_LIBRARIES})
add_dependencies(light_battery_node ${catkin_EXPORTED_TARGETS})

install(TARGETS light_node light_battery_node
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install( DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
