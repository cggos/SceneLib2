PROJECT("SceneLib2")

CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/CMakeModules/")

find_package( OpenCV )
if( OpenCV_FOUND )
    include_directories( ${OpenCV_INCLUDE_DIRS} )
    link_libraries( ${OpenCV_LIBS} )
endif()

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# Overide with cmake -DCMAKE_BUILD_TYPE=Release {dir}
IF(NOT CMAKE_BUILD_TYPE)
    MESSAGE("Build type not set (defaults to debug)")
    MESSAGE("-DCMAKE_BUILD_TYPE=Release for release")
#    SET(CMAKE_BUILD_TYPE Debug)
    SET(CMAKE_BUILD_TYPE Release)
ENDIF()

STRING(TOLOWER ${PROJECT_NAME} LIBRARY_NAME)

ADD_SUBDIRECTORY(${LIBRARY_NAME})
ADD_SUBDIRECTORY(examples)

