cmake_minimum_required(VERSION 3.20.0)

project(Example LANGUAGES CXX)

find_package(spdlog CONFIG REQUIRED)

set(CMAKE_CXX_STANDARD 20)

FILE(GLOB_RECURSE SRC_FILES "src/*.cpp" "src/*.h")
add_executable(${PROJECT_NAME} ${SRC_FILES})

target_link_libraries(${PROJECT_NAME} PRIVATE
    spdlog::spdlog)
