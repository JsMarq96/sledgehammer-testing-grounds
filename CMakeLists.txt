cmake_minimum_required(VERSION 3.21)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

project(sledgehammer_test)

file(GLOB H_SOURCES "src/*.h")
file(GLOB C_SOURCES "src/*.c")
file(GLOB SUBFOLDER_H_SOURCES "src/*/*.h")
file(GLOB SUBFOLDER_C_SOURCES "src/*/*.c")

add_executable(sledgehammer_test ${C_SOURCES} ${H_SOURCES} ${SUBFOLDER_H_SOURCES} ${SUBFOLDER_C_SOURCES})

set_target_properties(sledgehammer_test PROPERTIES C_STANDARD 23 LINKER_LANGUAGE C OUTPUT_NAME "phys_sandbox")

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_INSTALL OFF CACHE BOOL "" FORCE)
add_subdirectory(libraries/glfw)

add_subdirectory(libraries/gl3w)

add_subdirectory(libraries/sledgehammer)
target_link_libraries(sledgehammer_test cglm sledgehammer glfw gl3w)