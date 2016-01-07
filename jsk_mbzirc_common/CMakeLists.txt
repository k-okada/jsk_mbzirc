cmake_minimum_required(VERSION 2.8.3)
project(jsk_mbzirc_common)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp gazebo_ros dynamic_reconfigure)
include_directories(include ${catkin_INCLUDE_DIRS})


###################################
## catkin specific configuration ##
###################################
catkin_package(
    INCLUDE_DIRS include
    LIBRARIES
    CATKIN_DEPENDS roscpp gazebo_ros dynamic_reconfigure
    DEPENDS gazebo
)

find_package(gazebo REQUIRED)
link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS})

add_library(mbzirc_gazebo_truck_plugin src/mbzirc_gazebo_truck_plugin.cpp)
target_link_libraries(mbzirc_gazebo_truck_plugin ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})



#############
## Install ##
#############
install(TARGETS mbzirc_gazebo_truck_plugin
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)


#############
## Testing ##
#############
