cmake_minimum_required(VERSION 3.5)

# Set a default C++ compile flag
# 添加CXX编译控制符-DX2，缓冲CACHE类型，强制FORCE设置
# 直接使用${CMAKE_CXX_FLAGS }变量，C语言是${CMAKE_C_FLAGS}，在其中不断添加新的控制符，使用-D开头，类似于命令行传递值，这时候这个标志会传递到C++程序中，表示已经定义
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DEX2" CACHE STRING "Set C++ Compiler Flags" FORCE)

# Set the project name
project (compile_flags)

# Add an executable
add_executable(cmake_examples_compile_flags main.cpp)

# 直接将EX3导入到C程序中
target_compile_definitions(cmake_examples_compile_flags 
    PRIVATE EX3
)
# 除此之外还可以在命令行中传递：
# cmake .. -DCMAKE_CXX_FLAGS="-DEX2 -DEX2"


set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)