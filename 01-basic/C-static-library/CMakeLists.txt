# cmake_minimum_required(VERSION 3.5)

# project(hello_library)

# ############################################################
# # Create a library
# ############################################################

# #Generate the static library from the library sources
# # 生成静态库，通过add_library函数导入库源码，第一个参数时target，这里是库名称xxx，最后生成的也是libxxx.a，
# # 第二个参数是类型STATIC|SHARED|MODULE，
# # 第三个参数是源文件
# add_library(hello_library STATIC 
#     src/Hello.cpp
# )

# target_include_directories(hello_library
#     PUBLIC 
#         ${PROJECT_SOURCE_DIR}/include
# )

# set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

# ############################################################
# # Create an executable
# ############################################################

# # Add an executable with the above sources
# add_executable(hello_binary 
#     src/main.cpp
# )

# # link the new hello_library target with the hello_binary target
# target_link_libraries( hello_binary
#     PRIVATE 
#         hello_library
# )

# set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)





############################################################
# 测试外部工程使用静态库的CMakeLists
############################################################
cmake_minimum_required(VERSION 3.5)

project(hello_library)

############################################################
# Create an executable
############################################################

# 有时编译程序时想添加一些编译选项，如-Wall，-std=c++11等，就可以使用add_compile_options来进行操作
add_compile_options(-std=c++11 -Wall -g)

# Add an executable with the above sources
add_executable(hello_binary 
    src/main.cpp
)

# link the new hello_library target with the hello_binary target
target_link_libraries( hello_binary
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/lib/libhello_library.a
)
target_include_directories( hello_binary
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

