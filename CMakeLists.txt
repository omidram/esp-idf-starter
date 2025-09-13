# Define the project name and version
cmake_minimum_required(VERSION 3.16)
set(PROJECT_NAME esp-idf-starter)
project(${PROJECT_NAME})

# Include the ESP-IDF build system
include($ENV{IDF_PATH}/tools/cmake/project.cmake)

# Add the main component
add_subdirectory(main)

# Add other components as needed
add_subdirectory(components/app_core)
add_subdirectory(components/app_net)
add_subdirectory(components/app_ota)
