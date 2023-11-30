cmake_minimum_required(VERSION 3.5)

# Set the project name
project ("hash")


# # find a boost install with the libraries filesystem and system
# find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)

# # check if boost was found
# if(Boost_FOUND)
#     message ("boost found")
# else()
#     message (FATAL_ERROR "Cannot find Boost")
# endif()

# Add an executable
add_executable(hash main.cpp)

target_include_directories(hash
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)

# link against the boost libraries
target_link_libraries( hash
    PUBLIC
        ${PROJECT_SOURCE_DIR}/install/lib/libmbedtls.a
        ${PROJECT_SOURCE_DIR}/install/lib/libmbedcrypto.a  # 直接使用libmbedcrypto.a库文件，在系统目录下
)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)