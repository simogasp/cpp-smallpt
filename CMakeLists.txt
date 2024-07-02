cmake_minimum_required(VERSION 3.15)

project(smallpt LANGUAGES CXX)

option(USE_OPENMP "Use OpenMP" OFF)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(smallpt src/cpp-smallpt.cpp)

target_include_directories(smallpt PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src)
if(USE_OPENMP)
    find_package(OpenMP REQUIRED)
    target_link_libraries(smallpt OpenMP::OpenMP_CXX)
endif ()
