cmake_minimum_required(VERSION 3.10)

# Set the project name
project(pro-oneTBB)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# add a vs2022 solution folder
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

macro(add_fig)
    set(oneValueArgs NAME FOLDER)
    set(multiValueArgs SOURCES DEFINES DEPENDS)
    cmake_parse_arguments(fig "" "${oneValueArgs}" "${multiValueArgs}" ${ARGN})
    message(STATUS, "DEMO_NAME: ${fig_NAME}")

    include_directories($ENV{TBBROOT}/include $ENV{DPL_ROOT}/include)
    link_directories($ENV{TBBROOT}/lib $ENV{DPL_ROOT}/lib)

    # define maco to avoid duplicate code
    # Add the executable
    add_executable(tbb_${fig_NAME} ${fig_SOURCES})
    set_property(TARGET tbb_${fig_NAME} PROPERTY VS_DEBUGGER_ENVIRONMENT "PATH=%PATH%;$ENV{TBBROOT}/bin")
    set_property(TARGET tbb_${fig_NAME} PROPERTY FOLDER ${fig_FOLDER})
endmacro()

if (MSVC)
    message("make sure run \"C:\\Program Files (x86)\\Intel\\oneAPI\\setvars.bat\" before build")
    message(STATUS "DPL_ROOT: $ENV{DPL_ROOT}")

    find_package(TBB REQUIRED PATHS $ENV{TBBROOT}/lib/cmake/tbb)
    find_package(oneDPL REQUIRED PATHS $ENV{DPL_ROOT}/lib/cmake/oneDPL)

    # display TBB variables
    message(STATUS "TBB_IMPORTED_TARGETS: ${TBB_IMPORTED_TARGETS}")
endif()
add_subdirectory(ch01)
add_subdirectory(ch02)
