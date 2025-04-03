# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)

# Set the project name
project(image_cluster C)


find_package(PkgConfig REQUIRED)


pkg_check_modules(ISIO REQUIRED ImageStreamIO)


message("ISIO_LIBRARIES    :  ${ISIO_LIBRARIES}")
message("ISIO_INCLUDE_DIRS :  ${ISIO_INCLUDE_DIRS}")
message("ISIO_LIBRARY_DIRS :  ${ISIO_LIBRARY_DIRS}")
message("ISIO_CFLAGS       :  ${ISIO_CFLAGS}")

link_directories(${ISIO_LIBRARY_DIRS})

# Add an executable
add_executable(imclust src/imcluster.c)

target_link_libraries(imclust ${ISIO_LIBRARIES})
target_include_directories(imclust PUBLIC ${ISIO_INCLUDE_DIRS})


