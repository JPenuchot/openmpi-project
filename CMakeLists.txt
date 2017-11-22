cmake_minimum_required(VERSION 2.8.9)
project(mpi-training)

# Ckecking for packages
find_package(MPI REQUIRED)
#find_package(Boost REQUIRED)
#FIND_PACKAGE(Boost 1.4 COMPONENTS mpi serialization REQUIRED)

file(GLOB_RECURSE SOURCES "src/*.cpp")
add_executable(prog ${SOURCES})
set_target_properties(prog PROPERTIES COMPILE_FLAGS "-O3 -std=c++14")

#	Setting compiler to clang

#SET(CMAKE_C_COMPILER /usr/bin/clang)
#SET(CMAKE_CXX_COMPILER /usr/bin/clang++)

#	Uncomment to enable SIMD instructions
#set_target_properties(prog PROPERTIES COMPILE_FLAGS "-msse4.2 -mavx2 -mfma")

#	Adding includes
include_directories(${MPI_INCLUDE_PATH})

# Linking libraries
target_link_libraries(prog ${MPI_LIBRARIES})

#	Adding flags

if(MPI_LINK_FLAGS)
  set_target_properties(prog PROPERTIES
    LINK_FLAGS "${MPI_LINK_FLAGS}")
endif()

if(MPI_COMPILE_FLAGS)
  set_target_properties(prog PROPERTIES
    COMPILE_FLAGS "${MPI_COMPILE_FLAGS}")
endif()
