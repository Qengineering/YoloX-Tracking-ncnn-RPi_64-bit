cmake_minimum_required(VERSION 3.0 FATAL_ERROR)

project(YoloX_Track)

macro(use_cxx11)
  if (CMAKE_VERSION VERSION_LESS "3.1")
    if (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
      set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")
    endif ()
  else ()
    set (CMAKE_CXX_STANDARD 17)
  endif ()
endmacro(use_cxx11)

find_package(OpenCV REQUIRED)                              

set(SOURCES src/BYTETracker.cpp src/STrack.cpp src/kalmanFilter.cpp src/lapjv.cpp src/utils.cpp src/yoloX.cpp)

set(EXTRA_LIBS ${OpenCV_LIBS} /usr/local/lib/ncnn/libncnn.a)

set(EXECUTABLE_OUTPUT_PATH "../")

include_directories(include ${OpenCV_INCLUDE_DIRS} /usr/local/include/ncnn /usr/local/include/eigen3)

add_link_options(-fopenmp -lgomp -ldl -rdynamic -lpthread -pthread -march=armv8-a)

add_executable(YoloX_Track ${SOURCES})

target_link_libraries(YoloX_Track ${EXTRA_LIBS})