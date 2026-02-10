cmake_minimum_required(VERSION 3.10)

project(my_cmake)
set(CMAKE_CXX_STANDARD 11)

# 头文件路径
include_directories(${PROJECT_SOURCE_DIR}/include)

# 可执行文件输出目录
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

#指定动态库输出目录
# set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

# 动态库和可执行文件输出目录
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin) # windows

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin) # linux

#静态库
# set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY )

# 源文件
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)

# 1️⃣ 生成动态库
add_library(common SHARED ${SRC_LIST})

# 设置动态库的头文件路径 ，因为依赖这些库 ）
target_include_directories(common
    PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# 2️⃣ 生成可执行文件（注意：不再直接用 SRC_LIST）
add_executable(my_hello  
${PROJECT_SOURCE_DIR}/src/main.cpp
)

# 3️⃣ 链接动态库
target_link_libraries(my_hello
   PUBLIC
    common
)
