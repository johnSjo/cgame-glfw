set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

cmake_minimum_required(VERSION 3.30)

project(cgame-glfw)

# find_package(GLFW3 REQUIRED)
find_package(OpenGL REQUIRED)

# if(GLFW3_FOUND)
#   message(STATUS "GLFW3 found: ${GLFW3_LIBRARIES}")
#   message(STATUS "GLFW3 includes: ${GLFW3_INCLUDE_DIRS}")
# else()
#   message(FATAL_ERROR "GLFW3 not found.")
# endif()

include_directories(~/development/libraries/glfw/include/ ./libs/glad/include/ ./libs/linmath.h/)

include_directories(${GLFW3_INCLUDE_DIRS} ${OPENGL_INCLUDE_DIR})

add_library(glad ./libs/glad/src/gl.c)

add_executable(cgame src/main.c ./libs/glad/src/gl.c)

# set(GLFW3_LIBRARIES ~/development/libraries/glfw/build/src/libglfw3.a)
set(GLFW3_LIBRARIES /Users/john.sjostrom/development/libraries/glfw/build/src/libglfw3.a)
target_link_libraries(cgame ${GLFW3_LIBRARIES} ${OPENGL_LIBRARIES} "-framework Cocoa" "-framework Foundation" "-framework IOKit" glad)

# message(STATUS "CMAKE_LIBRARY_PATH: ${CMAKE_LIBRARY_PATH}")
