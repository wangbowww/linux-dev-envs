cmake_minimum_required(VERSION 3.16)
project(test LANGUAGES CXX)


set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# 只编译一个源文件：通过 -DTARGET_CPP=xxx.cpp 传入，默认 a.cpp
set(TARGET_CPP "a.cpp" CACHE STRING "Source file under src/ to build, for example a.cpp")
set(SRC_FILE "${PROJECT_SOURCE_DIR}/src/${TARGET_CPP}")

if(NOT EXISTS "${SRC_FILE}")
    message(FATAL_ERROR "Source file not found: ${SRC_FILE}")
endif()

get_filename_component(TARGET_NAME "${TARGET_CPP}" NAME_WE)
add_executable(${TARGET_NAME} "${SRC_FILE}")

# 可执行文件输出到 bin 目录
set_target_properties(${TARGET_NAME} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/bin"
)
