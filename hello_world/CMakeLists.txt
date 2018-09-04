cmake_minimum_required(VERSION 3.4.3)

project(hello_world)

find_package(LLVM REQUIRED CONFIG)
message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

set(SOURCE_FILES hello_world.cpp)

set(CMAKE_CXX_FLAGS
    "${CMAKE_CXX_FLAGS} -std=c++11 -Wno-deprecated-declarations")

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

add_executable(hello_world ${SOURCE_FILES})

target_link_libraries(hello_world
                      LLVMCore
                      LLVMSupport
                      LLVMBitWriter
                      LLVMIRReader)
