cmake_minimum_required(VERSION 3.19)

project(your-project-name)

set(CMAKE_CXX_STANDARD 20)

find_package(spdlog CONFIG REQUIRED)

file(GLOB_RECURSE PROJECT_SOURCES "src/*.cpp")
file(GLOB_RECURSE PROJECT_HEADERS "src/*.hpp")

add_executable(${PROJECT_NAME} ${PROJECT_SOURCES} ${PROJECT_HEADERS})

target_link_libraries(${PROJECT_NAME} PRIVATE spdlog::spdlog)

if(MSVC)
    set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${PROJECT_NAME})
    add_compile_options(/W4 /WX /permissive- /analyze /EHsc 
        /Zc:preprocessor /Zc:inline /Zc:strictStrings /Zc:rvalueCast
        /external:anglebrackets /external:W0 /analyze:external-)
endif()
