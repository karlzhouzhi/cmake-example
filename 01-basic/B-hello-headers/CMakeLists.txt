# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)

# Set the project name
project (hello_headers)

# Create a sources variable with a link to all cpp files to compile
# 新建一个SOURCE的变量（在多源码情况下可以建立多个不同的名称），该变量的值为一个“数组”
# 接下来在生成可执行文件函数add_executable中使用该变量，在多个变量情况下可以在末尾继续添加，
# 也可以使用file命令file(GLOB SOURCES "src/*.cpp")通过搜索通配符添加，
# 也可以使用aux_source_directory(src SOURCES)添加
# set(SOURCES
#     src/Hello.cpp
#     src/main.cpp
# )
# file(GLOB SOURCES "src/*.cpp")
aux_source_directory(src SOURCES)

# Add an executable with the above sources
add_executable(hello_headers ${SOURCES})

# Set the directories that should be included in the build command for this target
# when running g++ these will be included as -I/directory/path/
# 链接头文件，使用target_include_directories函数，
# 该函数第一个变量是目标target，这里指可执行文件，
# 之后是PRIVATE|PUBLIC|INTERFACE，顾名思义这是指作用域，之后再解释，
# 最后一个参数是路径，用PROJECT_SOURCE_DIR指向路径
target_include_directories(hello_headers
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)