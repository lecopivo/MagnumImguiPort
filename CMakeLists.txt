cmake_minimum_required(VERSION 3.7)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/modules/")

add_definitions(-std=c++14)

find_package(Magnum REQUIRED
  Shaders
  Sdl2Application)

include_directories(${SDL2_INCLUDE_DIR})

add_subdirectory(src)

