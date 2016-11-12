cmake_minimum_required(VERSION 2.8.3)
project(thermal_image_proc)

find_package(catkin REQUIRED COMPONENTS cv_bridge dynamic_reconfigure image_transport sensor_msgs)
find_package(OpenCV REQUIRED)

catkin_package(
  LIBRARIES ${PROJECT_NAME}
  DEPENDS opencv2
  )

include_directories(${catkin_INCLUDE_DIRS})

## Declare a cpp executable
add_executable(thermal_image_proc_node src/thermal_image_proc.cpp)

## Specify libraries to link a library or executable target against
target_link_libraries(thermal_image_proc_node
  ${catkin_LIBRARIES}
  ${OpenCV_LIBS}
)

#############
## Install ##
#############

## Mark executables and/or libraries for installation
install(TARGETS thermal_image_proc_node
 ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
 LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
 RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
