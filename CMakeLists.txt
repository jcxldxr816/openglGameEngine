cmake_minimum_required(VERSION 3.10)
project(openglGameEngine)

set(CMAKE_CXX_STANDARD 17)

# Use pkg-config to find GLFW
find_package(PkgConfig REQUIRED)
pkg_check_modules(GLFW REQUIRED glfw3)

add_executable(openglGameEngine src/main.cpp)

target_include_directories(openglGameEngine PRIVATE ${GLFW_INCLUDE_DIRS})
target_link_libraries(openglGameEngine PRIVATE ${GLFW_LIBRARIES})
target_link_options(openglGameEngine PRIVATE ${GLFW_LDFLAGS})

# Optionally, add OpenGL
find_package(OpenGL REQUIRED)
target_link_libraries(openglGameEngine PRIVATE OpenGL::GL)
