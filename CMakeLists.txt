cmake_minimum_required(VERSION 3.12)
project(asio VERSION 1.22.0)

file(GLOB_RECURSE TARGET_SOURCE_FILES
    "${PROJECT_SOURCE_DIR}/include/**.hpp"
)
include_directories(${PROJECT_SOURCE_DIR}/include)
add_library(${PROJECT_NAME} INTERFACE ${TARGET_SOURCE_FILES})
target_include_directories(${PROJECT_NAME} INTERFACE
    "${PROJECT_SOURCE_DIR}/include"
)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_20)
if (NOT MSVC)
    target_compile_options(${PROJECT_NAME} PRIVATE
        "-Wall"
        "-Wextra"
        "-Wconversion"
        "-Wpedantic"
        "-Werror"
    )
else()
    target_compile_options(${PROJECT_NAME} PRIVATE
        "/W4"
        "/WX"
    )
endif()
source_group(TREE "${CMAKE_CURRENT_LIST_DIR}" FILES ${TARGET_SOURCE_FILES})

