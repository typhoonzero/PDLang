cmake_minimum_required(VERSION 3.0)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/Paddle/cmake")
set(PADDLE_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Paddle)
set(PADDLE_BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR})

project(pdlang CXX C)

set(THIRD_PARTY_PATH "${CMAKE_BINARY_DIR}/third_party" CACHE STRING
  "A path setting third party libraries download & build directories.")

# =============== External Deps =================
include(external/boost)
include(external/eigen)
include(external/gflags)
include(external/glog)
include(external/gtest)
include(external/zlib)
include(external/protobuf)
include(external/snappy)
include(external/snappystream)
include(external/warpctc)
include(external/openblas)
include(external/mkldnn)
include(external/threadpool)

# =============== Global Config =================
include(configure)
include(generic)
include_directories("${PADDLE_SOURCE_DIR}")

# =============== Patch framework.proto =================


# =============== Compile Code =================
add_subdirectory("Paddle/paddle/fluid/string")
add_subdirectory("Paddle/paddle/fluid/memory")
add_subdirectory("Paddle/paddle/fluid/recordio")
add_subdirectory("Paddle/paddle/fluid/platform")
add_subdirectory("Paddle/paddle/fluid/operators")
add_subdirectory("Paddle/paddle/fluid/framework")

# Modified framework directory
add_subdirectory("pdlang")

