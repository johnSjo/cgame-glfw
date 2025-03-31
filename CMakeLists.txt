cmake_minimum_required(VERSION 3.25)
project(cgame-glfw)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

# Find OpenGL
find_package(OpenGL REQUIRED)

# Set Include Paths
set(GLFW_DIR "${CMAKE_SOURCE_DIR}/libs/glfw")
set(GLAD_DIR "${CMAKE_SOURCE_DIR}/libs/glad")
set(LINMATH_DIR "${CMAKE_SOURCE_DIR}/libs/linmath.h")
set(GFXLIB_DIR "${CMAKE_SOURCE_DIR}/libs/gfxlib")

# Define Executable
add_executable(cgame src/main.c)

# Create glad Library
add_library(glad ${GLAD_DIR}/src/gl.c)
target_include_directories(glad PUBLIC ${GLAD_DIR}/include)

# Create gfxlib Library
add_library(gfxlib ${GFXLIB_DIR}/src/gfxlib.c)
target_include_directories(gfxlib PUBLIC ${GFXLIB_DIR}/include)

# Set Include Directories for Executable
target_include_directories(cgame PRIVATE ${GLFW_DIR}/include ${LINMATH_DIR})

# Link Dependencies
target_link_directories(cgame PRIVATE ${GLFW_DIR}/build/src)
target_link_libraries(cgame PRIVATE glfw3 OpenGL::GL glad gfxlib m)

