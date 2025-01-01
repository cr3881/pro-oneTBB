cmake_minimum_required(VERSION 3.10)

# Set the project name
project(pro-oneTBB)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

if (MSVC)
    message("make sure run \"C:\\Program Files (x86)\\Intel\\oneAPI\\setvars.bat\" before build")
    message(STATUS "DPL_ROOT: $ENV{DPL_ROOT}")

    find_package(TBB REQUIRED PATHS $ENV{TBBROOT}/lib/cmake/tbb)
    find_package(oneDPL REQUIRED PATHS $ENV{DPL_ROOT}/lib/cmake/oneDPL)

    # display TBB variables
    message(STATUS "TBB_IMPORTED_TARGETS: ${TBB_IMPORTED_TARGETS}")

    add_subdirectory(ch01)
endif()