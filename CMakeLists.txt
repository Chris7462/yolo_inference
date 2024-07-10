cmake_minimum_required(VERSION 3.16)
project(yolo_cpp)

# CUDA
set(CUDA_TOOLKIT_ROOT_DIR "/usr/local/cuda")
#find_package(CUDA 11 REQUIRED)
find_package(CUDA REQUIRED)

set(CMAKE_CUDA_STANDARD 17)
set(CMAKE_CUDA_STANDARD_REQUIRED ON)
# !CUDA

# OpenCV
find_package(OpenCV REQUIRED)
# !OpenCV

add_executable(yolo_cpp
  src/inference.cpp
  src/main.cpp)

target_include_directories(yolo_cpp PRIVATE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
  ${OpenCV_INCLUDE_DIRS})

target_link_libraries(yolo_cpp
  ${OpenCV_LIBS})
