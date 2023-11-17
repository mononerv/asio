cmake_minimum_required(VERSION 3.12)
project(asio VERSION 1.28.0)

# Install directory setup
include(GNUInstallDirs)
set(INC_DIR ${CMAKE_INSTALL_INCLUDEDIR})

file(GLOB_RECURSE HEADER_FILES
    "${PROJECT_SOURCE_DIR}/include/asio/**.hpp"
)
# Interface library
add_library(asio INTERFACE)
target_include_directories(asio
    INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:${INC_DIR}>
)
add_library(asio::asio ALIAS asio)

