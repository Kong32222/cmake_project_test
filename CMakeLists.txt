cmake_minimum_required(VERSION 3.10)

project(my_cmake)
set(CMake_CXX_STANDARD 11)

include_directories(${PROJECT_SOURCE_DIR}/include)

#设置输出目录
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

#
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)

add_executable(
    my_hello
    ${SRC_LIST}
)