cmake_minimum_required(VERSION 2.8.3)
project(ros_text_speech)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp std_msgs sound_play)

catkin_package(
  CATKIN_DEPENDS roscpp std_msgs sound_play
)

include_directories(${catkin_INCLUDE_DIRS})

###########
## Build ##
###########

## Declare a cpp executable
add_executable(textspeech src/speech_database.cpp)
target_link_libraries(textspeech ${catkin_LIBRARIES})

## Specify libraries to link a library or executable target against
target_link_libraries(textspeech   ${catkin_LIBRARIES})
target_link_libraries(textspeech curl)
target_link_libraries(textspeech jansson)

#############
## Install ##
#############

install(PROGRAMS
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(TARGETS textspeech
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
