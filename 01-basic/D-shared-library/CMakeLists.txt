# cmake_minimum_required(VERSION 3.5)

# project(hello_library_demo)

# ############################################################
# # Create a library
# ############################################################

# #Generate the shared library from the library sources
# add_library(hello_library SHARED 
#     src/Hello.cpp
# )
# add_library(hello::library ALIAS hello_library) # ALIAS关键字，内部重命名

# target_include_directories(hello_library
#     PUBLIC 
#         ${PROJECT_SOURCE_DIR}/include
# )

# # 有时编译程序时想添加一些编译选项，如-Wall，-std=c++11等，就可以使用add_compile_options来进行操作
# add_compile_options(-std=c++11 -Wall -g)

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
#         hello::library
# )

# set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)



############################################################
# 第三方项目使用动态链接库
############################################################

cmake_minimum_required(VERSION 3.5)

project(hello_library_demo)


# 有时编译程序时想添加一些编译选项，如-Wall，-std=c++11等，就可以使用add_compile_options来进行操作
add_compile_options(-std=c++11 -Wall -g)

############################################################
# Create an executable
############################################################

# Add an executable with the above sources
add_executable(hello_binary
    src/main.cpp
)

# link the new hello_library target with the hello_binary target
target_link_libraries( hello_binary
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/lib/libhello_library.dylib
)
target_include_directories(hello_binary
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include
)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)