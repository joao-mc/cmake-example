# Set cmake minimum version.
cmake_minimum_required(VERSION 3.14)

# Set the project details.
set(PROJECT_NAME cmake-example)
project(${PROJECT_NAME} LANGUAGES CXX)

# Disable in-source builds.
set(CMAKE_DISABLE_IN_SOURCE_BUILD ON)
set(CMAKE_DISABLE_SOURCE_CHANGES ON)

# Set build type to debug by default.
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Debug)
endif()

# Define the executable.
add_executable(${PROJECT_NAME})

# Set C++ standard.
set_target_properties(${PROJECT_NAME} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
    CXX_EXTENSIONS OFF
)

# Add source files.
add_subdirectory(src)
# Add third party libraries.
add_subdirectory(lib)

# Find dependencies.
find_package(OpenGL COMPONENTS OpenGL REQUIRED)

# Include and link against dependencies.
target_link_libraries(${PROJECT_NAME} PRIVATE OpenGL::GL sfml-graphics sfml-window)
