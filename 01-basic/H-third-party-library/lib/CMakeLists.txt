include(FetchContent)
set(FETCHCONTENT_QUIET FALSE)

if ("${MBEDCRYPTO_PATH}" STREQUAL "DOWNLOAD")
    find_package(Git)
    FetchContent_Declare(mbedcrypto
        GIT_REPOSITORY ${MBEDCRYPTO_GIT_REMOTE}
        GIT_TAG ${MBEDCRYPTO_VERSION}
        GIT_SHALLOW TRUE
        GIT_PROGRESS TRUE
        GIT_SUBMODULES ""
    )

    FetchContent_GetProperties(mbedcrypto)

    if(NOT mbedcrypto_POPULATED)
        FetchContent_Populate(mbedcrypto)
        set(MBEDCRYPTO_PATH ${mbedcrypto_SOURCE_DIR} CACHE PATH "Path to mbed-crypto (or DOWNLOAD to get automatically" FORCE)
    endif()
endif()
