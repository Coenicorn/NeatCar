cmake_minimum_required(VERSION 4.1)

project(
    "VisualAstar"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CXX_COMPILE_FLAGS "-Wall -Wpedantic -Wextra -g")

# zed cmake extension compatibility...?
# https://github.com/k0tran/zed_neocmake
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# global include directory
include_directories(${CMAKE_SOURCE_DIR}/include)

# raylib library
set(PLATFORM "Desktop")
set(CMAKE_BUILD_TYPE "Debug")

add_subdirectory(${CMAKE_SOURCE_DIR}/lib/raylib)

add_subdirectory(${CMAKE_SOURCE_DIR}/src)
target_include_directories(
    NeatCar
    PUBLIC ${CMAKE_SOURCE_DIR}/lib/raylib/src
)

target_link_libraries(
    NeatCar
    PUBLIC raylib m
)
