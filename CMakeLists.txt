cmake_minimum_required(VERSION 3.21)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

project(sledgehammer_test)

file(GLOB H_SOURCES "src/*.h")
file(GLOB C_SOURCES "src/*.c")
file(GLOB SUBFOLDER_H_SOURCES "src/*/*.h")
file(GLOB SUBFOLDER_C_SOURCES "src/*/*.c")

add_executable(sledgehammer_test ${C_SOURCES} ${H_SOURCES} ${SUBFOLDER_H_SOURCES} ${SUBFOLDER_C_SOURCES})

set_target_properties(sledgehammer_test PROPERTIES C_STANDARD 23 LINKER_LANGUAGE C OUTPUT_NAME "phys_sandbox")

add_subdirectory(libraries/cglm)
add_subdirectory(libraries/)
target_link_libraries(sledgehammer_test cglm)