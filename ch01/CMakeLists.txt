
cmake_minimum_required(VERSION 3.10)

# Set the project name
project(Ch01)

include_directories($ENV{TBBROOT}/include $ENV{DPL_ROOT}/include)
link_directories($ENV{TBBROOT}/lib $ENV{DPL_ROOT}/lib)

macro(add_fig)
    set(oneValueArgs NAME)
    set(multiValueArgs SOURCES DEFINES DEPENDS)
    cmake_parse_arguments(fig "" "${oneValueArgs}" "${multiValueArgs}" ${ARGN})
    message(STATUS, "DEMO_NAME: ${fig_NAME}")
    # define maco to avoid duplicate code
    # Add the executable
    add_executable(tbb_${fig_NAME} ${fig_NAME}.cpp)
    set_property(TARGET tbb_${fig_NAME} PROPERTY VS_DEBUGGER_ENVIRONMENT "PATH=%PATH%;$ENV{TBBROOT}/bin")
endmacro()

add_fig(NAME fig_1_04)
add_fig(NAME fig_1_05)
add_fig(NAME fig_1_07)
add_fig(NAME fig_1_10)
add_fig(NAME fig_1_11)
add_fig(NAME fig_1_12)