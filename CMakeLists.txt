cmake_minimum_required(VERSION 2.8.12)

project(libcaesium)

set(CMAKE_MACOSX_RPATH 1)
set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)

# The version number.
set(VERSION_MAJOR 0)
set(VERSION_MINOR 4)
set(VERSION_PATCH 0)

configure_file(
        "caesium/config.h.in"
        "${PROJECT_BINARY_DIR}/config.h"
)

link_directories(/usr/local/lib)

include_directories("${PROJECT_BINARY_DIR}")
if (NOT WIN32)
    include_directories(/opt/mozjpeg/include)
    include_directories(/usr/local/include)

    if(EXISTS /opt/mozjpeg/lib64)
        link_directories(/opt/mozjpeg/lib64)
    else()
        link_directories(/opt/mozjpeg/lib)
    endif()
else ()
    include_directories(C:\\mozjpeg\\include)
    include_directories(C:\\zopfli\\src)
endif()


add_subdirectory(caesium)
add_subdirectory(demo)


