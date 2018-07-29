cmake_minimum_required(VERSION 3.10)
project(demo)

set(CMAKE_CXX_STANDARD 17)
add_executable(demo main.cpp shader.h)

configure_file(vertex_shader.glsl vertex_shader.glsl COPYONLY)
configure_file(fragment_shader.glsl fragment_shader.glsl COPYONLY)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(GLEW REQUIRED CONFIG)

include_directories( ${OPENGL_INCLUDE_DIRS} )
target_link_libraries(demo glfw)
target_link_libraries(demo GLEW::GLEW)
target_link_libraries(demo ${OPENGL_gl_LIBRARY})