cmake_minimum_required(VERSION 3.16)

project(yolo_inference VERSION 1.0.0)

find_package(OpenCV REQUIRED)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Find OpenCV package
find_package(OpenCV REQUIRED)

# Define the library target
add_library(yolo_inference STATIC
  src/inference.cpp)

# Specify include directories for the target
target_include_directories(yolo_inference PRIVATE
  ${PROJECT_SOURCE_DIR}/include
  ${OpenCV_INCLUDE_DIRS})

# Link OpenCV libraries to the target
target_link_libraries(yolo_inference
  ${OpenCV_LIBS})

# # Optionally set properties for the library
# set_target_properties(yolo_inference PROPERTIES
#   VERSION ${PROJECT_VERSION}
#   SOVERSION 1
# )

# # Optionally create an alias target for convenience
# add_library(YoloInference::yolo_inference ALIAS yolo_inference)

# Optionally install the library
install(TARGETS yolo_inference
  EXPORT YoloInferenceTargets
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  INCLUDES DESTINATION include
)

# Install header files
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/yolo_inference
  DESTINATION include
)

# # Optionally export the targets for usage in other projects
# install(EXPORT YoloInferenceTargets
#   FILE YoloInferenceTargets.cmake
#   NAMESPACE YoloInference::
#   DESTINATION lib/cmake/YoloInference
# )

# # Optionally add a package configuration file for find_package support
# include(CMakePackageConfigHelpers)
# write_basic_package_version_file(
#   ${CMAKE_CURRENT_BINARY_DIR}/YoloCppConfigVersion.cmake
#   VERSION ${PROJECT_VERSION}
#   COMPATIBILITY AnyNewerVersion
# )

# configure_package_config_file(${PROJECT_SOURCE_DIR}/YoloCppConfig.cmake.in
#   ${CMAKE_CURRENT_BINARY_DIR}/YoloCppConfig.cmake
#   INSTALL_DESTINATION lib/cmake/YoloCpp
# )

# install(FILES
#   ${CMAKE_CURRENT_BINARY_DIR}/YoloCppConfig.cmake
#   ${CMAKE_CURRENT_BINARY_DIR}/YoloCppConfigVersion.cmake
#   DESTINATION lib/cmake/YoloCpp
# )
