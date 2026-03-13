cmake_minimum_required(VERSION 3.28)

project(cubemars-drivers C)

set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)

# Inference library

file(GLOB LIB_SOURCES src/*.c)

add_library(cubemars-drivers ${LIB_SOURCES})

target_include_directories(cubemars-drivers
PUBLIC
${PROJECT_SOURCE_DIR}/inc
)

# Example executable

file (GLOB EXAMPLE_SOURCES demo/*.c)

add_executable(demo ${EXAMPLE_SOURCES})

target_link_libraries(demo
    PRIVATE
        cubemars-drivers
)

# Compiler options and static analysis

add_compile_options(
    -Wall
    -Wextra
    -Wpedantic
    -Werror
    -Wshadow
    -Wconversion
    -Wformat=2
)