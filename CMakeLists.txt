# Define the project name
cmake_minimum_required(VERSION 3.15)
project(sdl-sample-project)


# Add all c++ source files under the src directory
file(GLOB SOURCES "src/*.cpp")
add_executable(${PROJECT_NAME} ${SOURCES})
# Add all headers files under the include directory
target_include_directories(${PROJECT_NAME} PRIVATE include)
# Add compiler errors/warnings flags
target_compile_options(${PROJECT_NAME} PRIVATE $<$<C_COMPILER_ID:MSVC>:/W4 /WX>)
target_compile_options(${PROJECT_NAME} PRIVATE $<$<NOT:$<C_COMPILER_ID:MSVC>>:-Wall -Wextra -pedantic -Werror>)
# Add SDL2 library
find_package(SDL2 REQUIRED)
target_link_libraries(${PROJECT_NAME} SDL2::Main)

add_executable(${PROJECT_NAME} src/main.cpp)
