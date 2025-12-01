cmake_minimum_required(VERSION 3.25)
project(aoc2025 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_compile_options(
  -Wall -Wextra -Wpedantic
  $<$<CXX_COMPILER_ID:GNU,Clang>:-Werror>
  $<$<CXX_COMPILER_ID:GNU>:-Wformat=2>
)

add_compile_options(
  $<$<CONFIG:Debug>:-fsanitize=address,undefined>
)

add_link_options(
  $<$<CONFIG:Debug>:-fsanitize=address,undefined>
)

find_program(CCACHE_PROGRAM ccache)
if(CCACHE_PROGRAM)
  set_property(GLOBAL PROPERTY RULE_LAUNCH_COMPILE "${CCACHE_PROGRAM}")
endif()

add_subdirectory(day01)
