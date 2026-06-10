cmake_minimum_required(VERSION 3.5)
cmake_policy(SET CMP0048 NEW)
project(pairs_point_lio_estimator_plugin)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  pairs_uav_managers
  pairs_uav_state_estimators
  )

set(LIBRARIES
  PairsUavStateEstimators_PointLio
  )

catkin_package(
  CATKIN_DEPENDS
  pairs_uav_managers
  pairs_uav_state_estimators
  )

find_package(pairs_uav_state_estimators REQUIRED)

###########
## Build ##
###########

add_library(PairsUavStateEstimators_PointLio
  src/point_lio_plugin.cpp
  )

add_dependencies(PairsUavStateEstimators_PointLio
  ${${PROJECT_NAME}_EXPORTED_TARGETS}
  ${catkin_EXPORTED_TARGETS}
  )

target_link_libraries(PairsUavStateEstimators_PointLio
  ${catkin_LIBRARIES}
  )

target_include_directories(PairsUavStateEstimators_PointLio
  PRIVATE
  ${catkin_INCLUDE_DIRS}
  )

## --------------------------------------------------------------
## |                           Install                          |
## --------------------------------------------------------------

install(TARGETS ${LIBRARIES}
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_GLOBAL_BIN_DESTINATION}
  )

install(DIRECTORY custom_configs
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  )

install(FILES estimator_plugins.xml
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  )
