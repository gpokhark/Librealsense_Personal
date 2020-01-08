# License: Apache 2.0. See LICENSE file in root directory.
# Copyright(c) 2019 Intel Corporation. All Rights Reserved.
#  minimum required cmake version: 3.1.0
cmake_minimum_required(VERSION 3.1.0)
project(rs-measure)

find_package(realsense2 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(OpenCV REQUIRED)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

set(DEPENDENCIES ${realsense2_LIBRARY} glfw ${OPENGL_LIBRARIES} ${OpenCV_LIBS})
include_directories(${realsense2_INCLUDE_DIR} ${OpenCV_INCLUDE_DIRS})

add_executable(rs-measure rs-measure.cpp example.hpp)
set_property(TARGET rs-measure PROPERTY CXX_STANDARD 11)
target_link_libraries(rs-measure ${DEPENDENCIES} Threads::Threads)

install(TARGETS rs-measure RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

