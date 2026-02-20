cmake_minimum_required(VERSION 3.16)
project(hello)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")

add_subdirectory(../SDL SDL-build EXCLUDE_FROM_ALL)

add_executable(hello WIN32 hello.c)

target_link_libraries(hello PRIVATE SDL3::SDL3)