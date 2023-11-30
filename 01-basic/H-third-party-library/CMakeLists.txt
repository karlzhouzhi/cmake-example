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





# ##############################################################
# # 使用git直接下载并使用                                         #
# ##############################################################
# cmake_minimum_required(VERSION 3.5)

# project(hash)

# # 导入MBEDTLS第三方库
# include(config/config.cmake)

# # 下载MBEDTLS库，路径保存在 MBEDCRYPTO_PATH 中
# add_subdirectory(${PROJECT_SOURCE_DIR}/lib)

# # 添加库的所有源码
# aux_source_directory(${MBEDCRYPTO_PATH}/library MBEDTLS_SOURCES)

# # 建立可执行文件目标
# add_executable(hash
#     ${CMAKE_CURRENT_LIST_DIR}/main.cpp
#     ${MBEDTLS_SOURCES}
# )

# # 添加头文件
# target_include_directories(hash
#     PUBLIC
#         ${PROJECT_SOURCE_DIR}/include
#         ${MBEDCRYPTO_PATH}/include
#         ${MBEDCRYPTO_PATH}/library
# )