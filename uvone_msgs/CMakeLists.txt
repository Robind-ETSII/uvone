cmake_minimum_required(VERSION 3.10.2)
project(uvone_msgs)
find_package(catkin REQUIRED COMPONENTS std_msgs message_generation)

add_message_files(
  FILES
  LightCmd.msg
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

catkin_package(
    CATKIN_DEPENDS message_runtime
)
