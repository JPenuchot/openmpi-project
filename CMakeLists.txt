cmake_minimum_required(VERSION 2.8.9)
project(mpi-training)

# Ckecking for packages
find_package(MPI REQUIRED)
#find_package(Boost REQUIRED)
#FIND_PACKAGE(Boost 1.4 COMPONENTS mpi serialization REQUIRED)

# Adding includes
include_directories(${MPI_INCLUDE_PATH})

file(GLOB SOURCE_DIRS "src__*")

foreach(SRCDIR ${SOURCE_DIRS})
  # Splitting directory's name into a list that will contain the name of the executable
  string(REPLACE "__" ";" SRCDIR_PARSED ${SRCDIR})
  list(GET SRCDIR_PARSED 1 EXEC_NAME)

  # Getting sources...
  file(GLOB_RECURSE SOURCES "${SRCDIR}/*.cpp")

  add_executable("prog-${EXEC_NAME}" ${SOURCES})

  # Linking libraries
  target_link_libraries("prog-${EXEC_NAME}" ${MPI_LIBRARIES})
  # Adding flags
  if(MPI_LINK_FLAGS)
    set_target_properties("prog-${EXEC_NAME}" PROPERTIES
      LINK_FLAGS "${MPI_LINK_FLAGS}")
  endif()
  if(MPI_COMPILE_FLAGS)
    set_target_properties("prog-${EXEC_NAME}" PROPERTIES
      COMPILE_FLAGS "${MPI_COMPILE_FLAGS}")
  endif()
endforeach(SRCDIR)

# Uncomment to enable SIMD instructions
#set_target_properties(prog PROPERTIES COMPILE_FLAGS "-msse4.2 -mavx2 -mfma")

# Adding includes
include_directories(${MPI_INCLUDE_PATH})
