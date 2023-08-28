cmake_minimum_required(VERSION 3.5)
project(solar_system)

# Find required packages
find_package(OpenGL REQUIRED)

# Add subdirectories for dependencies
add_subdirectory(glfw)
include_directories(${CMAKE_SOURCE_DIR}/glew/include)
add_library(GLEW_STATIC ${CMAKE_SOURCE_DIR}/glew/src/glew.c)

# Include directories
include_directories(${OPENGL_INCLUDE_DIR})
include_directories(glfw/include)
include_directories(glm)

# Gather source files
file(GLOB SOURCE_FILES
        ${CMAKE_SOURCE_DIR}/src/*.cpp
        # Add other patterns if your source files are in different directories
)

# Set compiler flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -I/usr/local/include -O2 -Wall -Wextra -std=c++11")

# Add the executable and link libraries
add_executable(solar_system ${SOURCE_FILES})
target_link_libraries(solar_system glfw ${GLFW_LIBRARIES} ${OPENGL_LIBRARY} GLEW_STATIC)


