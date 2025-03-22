cmake_minimum_required(VERSION 3.10)
project(OpenGLProject)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

cmake_policy(SET CMP0072 NEW)

find_package(glfw3 REQUIRED)
find_package(OpenGL REQUIRED)

# Add GLAD
add_library(glad STATIC src/glad.c)
target_include_directories(glad PUBLIC include)

# Add executable
add_executable(main src/main.cpp)  # Ensure main.cpp is explicitly listed
target_include_directories(main PUBLIC include)
target_link_libraries(main glad glfw OpenGL::GL)
