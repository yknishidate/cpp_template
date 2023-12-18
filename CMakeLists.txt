cmake_minimum_required(VERSION 3.19)

project(your-project-name)

# Set C++20 standard
set(CMAKE_CXX_STANDARD 20)

# Find spdlog package
find_package(spdlog CONFIG REQUIRED)

# Add your source files under src/
file(GLOB_RECURSE PROJECT_SOURCES "src/*.cpp")
file(GLOB_RECURSE PROJECT_HEADERS "src/*.hpp")

# Define the executable with the source files
add_executable(${PROJECT_NAME} ${PROJECT_SOURCES} ${PROJECT_HEADERS})

# Link spdlog
target_link_libraries(${PROJECT_NAME} PRIVATE spdlog::spdlog)
