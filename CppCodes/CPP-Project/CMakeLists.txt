cmake_minimum_required(VERSION 3.16)
project(test LANGUAGES CXX)


set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# 只编译 src 目录下的所有 cpp 文件
file(GLOB SRC_FILES CONFIGURE_DEPENDS src/*.cpp)
add_executable(test ${SRC_FILES})

# 可执行文件输出到 bin 目录
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
