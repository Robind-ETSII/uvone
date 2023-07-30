cmake_minimum_required(VERSION 3.10.2)
project(uvone_description)

find_package(catkin)
catkin_package()

install(DIRECTORY launch meshes urdf robots
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
