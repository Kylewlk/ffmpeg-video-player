##
# CMake minimum required version for the project.
##
cmake_minimum_required(VERSION 3.11)

##
# FFmpeg-Video-Player C Project CMakeLists.txt.
##
project(FFmpeg_Video_Player)

add_compile_options("$<$<CXX_COMPILER_ID:MSVC>:/utf-8>")

set(CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/libs")

find_package(SDL2 REQUIRED)
set(SDL2_LIBRARIES SDL2::SDL2)
file(COPY "${CMAKE_CURRENT_SOURCE_DIR}/libs/SDL2-2.30.2/lib/x64/SDL2.dll" DESTINATION "${CMAKE_BINARY_DIR}/" )

set(FFMPEG_INCLUDE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}/libs/ffmpeg/include)
file(GLOB FFMPEG_LIBRARIES LIST_DIRECTORIES false "${CMAKE_CURRENT_SOURCE_DIR}/libs/ffmpeg/lib/*.lib")
file(GLOB ffmpeg_dll LIST_DIRECTORIES false "${CMAKE_CURRENT_SOURCE_DIR}/libs/ffmpeg/bin/*.dll")
file(COPY ${ffmpeg_dll} DESTINATION ${CMAKE_BINARY_DIR})


set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

add_compile_definitions(SDL_MAIN_HANDLED)

##
# Add subdirectories to the build.
##
add_subdirectory(tutorial01)
add_subdirectory(tutorial02)
add_subdirectory(tutorial03)
add_subdirectory(tutorial04)
add_subdirectory(tutorial05)
add_subdirectory(tutorial06)
add_subdirectory(tutorial07)
add_subdirectory(player)
