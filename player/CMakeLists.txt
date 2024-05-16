##
# CMake minimum required version for the project.
##
cmake_minimum_required(VERSION 3.11)

##
# player C Project CMakeLists.txt.
##
project(player C)

##
# Sets the C standard whose features are requested to build this target.
##
set(CMAKE_C_STANDARD 99)

add_executable(Player player.cpp)
target_include_directories(Player PRIVATE ${FFMPEG_INCLUDE_DIRS})
target_link_libraries(Player PRIVATE ${SDL2_LIBRARIES} ${FFMPEG_LIBRARIES})
