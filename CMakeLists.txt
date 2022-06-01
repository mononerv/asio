cmake_minimum_required(VERSION 3.12)
project(asio VERSION 1.22.0)
set(CMAKE_CXX_STANDARD 17)

# warnings and errors
if (NOT MSVC)
    string(JOIN " " CMAKE_CXX_FLAGS
        ${CMAKE_CXX_FLAGS}
        "-Wall"
        "-Wextra"
        "-Wconversion"
        "-Wpedantic"
        "-Werror"
    )
else()
    string(JOIN " " CMAKE_CXX_FLAGS
        ${CMAKE_CXX_FLAGS}
        "/W4"
        "/WX"
    )
endif()

file(GLOB_RECURSE TARGET_SOURCE_FILES
    "${PROJECT_SOURCE_DIR}/include/**.hpp"
)
include_directories(${PROJECT_SOURCE_DIR}/include)
add_library(${PROJECT_NAME} INTERFACE ${TARGET_SOURCE_FILES})
target_include_directories(${PROJECT_NAME} INTERFACE
    "${PROJECT_SOURCE_DIR}/include"
)
source_group(TREE "${CMAKE_CURRENT_LIST_DIR}" FILES ${TARGET_SOURCE_FILES})

