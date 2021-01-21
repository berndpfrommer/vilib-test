cmake_minimum_required(VERSION 3.10)

if (${CMAKE_VERSION} VERSION_LESS 3.15)
   project(vilib-test LANGUAGES CXX)
else()
   project(vilib-test LANGUAGES CXX CUDA)
endif()

find_package(vilib REQUIRED)
find_package(OpenCV COMPONENTS core imgproc features2d highgui)
find_package(CUDA REQUIRED)

message(STATUS "Found CUDA ${CUDA_VERSION_STRING} at ${CUDA_TOOLKIT_ROOT_DIR}")

file(GLOB_RECURSE VILIB_TEST_SOURCES
  src/*.cpp
  src/*.cu
  )

add_executable(vilib_tests ${VILIB_TEST_SOURCES})
include_directories(include)

target_link_libraries(vilib_tests
  vilib::vilib
  opencv_core opencv_imgproc opencv_features2d opencv_highgui
  ${CUDA_LIBRARIES})

install(TARGETS vilib_tests)


