cmake_minimum_required(VERSION 3.9)
project(workflow VERSION 1.23.0 LANGUAGES C CXX)

option(WORKFLOW_BUILD_TESTS "Build WorkFLow's unit tests" ON)
option(WORKFLOW_BUILD_BENCHMARKS "Build WorkFLow's benchmarks" ON)
option(WORKFLOW_INSTALL "Install WorkFlow's header and library" ON)

include(CheckIncludeFile)
check_include_file("unistd.h" HAVE_UNISTD_H)

include_directories("${PROJECT_BINARY_DIR}/include" "." "include")

if(BUILD_SHARED_LIBS)
  add_compile_options(-fvisibility=hidden)
endif(BUILD_SHARED_LIBS)

add_library(workflow "")
target_sources(workflow PRIVATE "src/api.cc")
