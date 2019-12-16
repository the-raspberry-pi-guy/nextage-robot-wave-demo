cmake_minimum_required(VERSION 2.8.3)
project(wave_demo)

find_package(catkin REQUIRED COMPONENTS
  exotica_python
  exotica_examples
  nextagea_description
  nextagea_moveit_config
)

catkin_package(
)


# install(PROGRAMS
#   scripts/my_python_script
#   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

