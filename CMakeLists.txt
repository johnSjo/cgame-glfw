set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

cmake_minimum_required(VERSION 3.25)

project(cgame-glfw)

find_package(OpenGL REQUIRED)

include_directories(./libs/glfw/include/ ./libs/glad/include/ ./libs/linmath.h/)

include_directories(${GLFW3_INCLUDE_DIRS} ${OPENGL_INCLUDE_DIR})

add_library(glad ./libs/glad/src/gl.c)

add_executable(cgame src/main.c ./libs/glad/src/gl.c)

set(GLFW3_LIBRARIES /home/john/dev/projects/cgame-glfw/libs/glfw/build/src/libglfw3.a)
target_link_libraries(cgame ${GLFW3_LIBRARIES} ${OPENGL_LIBRARIES} glad m)

