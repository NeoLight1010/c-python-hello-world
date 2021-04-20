set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "../bin")

cmake_minimum_required(VERSION 3.0.0)
project(python-c-test VERSION 0.1.0)

include(CTest)
enable_testing()

find_package(PkgConfig REQUIRED)

pkg_check_modules(PYTHON3 REQUIRED IMPORTED_TARGET python3-embed)

add_executable(python-c-test main.c)

target_link_libraries(
    python-c-test PUBLIC
    PkgConfig::PYTHON3
)

target_include_directories(
    python-c-test PUBLIC
    PYTHON3_INCLUDE_DIRS
)
    
set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

