cmake_minimum_required(VERSION 2.8.3)
project(hector_worldmodel_msgs)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS message_generation sensor_msgs geometry_msgs)

## Uncomment this if the package has a setup.py. This macro ensures
## modules and global scripts declared therein get installed
## See http://ros.org/doc/api/catkin/html/user_guide/setup_dot_py.html
# catkin_python_setup()

#######################################
## Declare ROS messages and services ##
#######################################

## Generate messages in the 'msg' folder
add_message_files(
  FILES
  ImagePercept.msg
  ObjectInfo.msg
  ObjectModel.msg
  Object.msg
  ObjectState.msg
  PerceptInfo.msg
  PosePercept.msg
)

## Generate services in the 'srv' folder
add_service_files(
  FILES
  AddObject.srv
  AddVictim.srv
  GetObjectModel.srv
  SetObjectName.srv
  SetObjectState.srv
  VerifyObject.srv
  VerifyPercept.srv
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES sensor_msgs geometry_msgs
)


###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
    INCLUDE_DIRS include
    LIBRARIES
    CATKIN_DEPENDS sensor_msgs geometry_msgs
    DEPENDS
)

###########
## Build ##
###########


#############
## Install ##
#############

# all install targets should use catkin DESTINATION variables
# See http://ros.org/doc/api/catkin/html/adv_user_guide/variables.html

## Mark cpp header files for installation
install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
  PATTERN ".svn" EXCLUDE
)
