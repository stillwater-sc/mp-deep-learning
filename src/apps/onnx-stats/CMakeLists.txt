cmake_minimum_required(VERSION 3.22)
set(app_name onnx-stats)
project(${app_name} CXX)

# Abseil requires at least C++17
set(CMAKE_CXX_STANDARD 20)

# Universal is a C++ header-only library, so we do not need to build anything
include_directories(${MPDL_ROOT_DIR}/ext/stillwater-sc/universal/include)
include_directories(${MPDL_ROOT_DIR}/ext/google/abseil-cpp)

# source files that make up the command
set(SOURCE_FILES
	onnx-stats.cpp
)

add_executable(${app_name} ${SOURCE_FILES})
set(folder "Applications/Mixed-Precision")
set_target_properties(${app_name} PROPERTIES FOLDER ${folder})

# Declare dependency on the absl::log library
target_link_libraries(${app_name} absl::log absl::strings)
install(TARGETS ${app_name} DESTINATION ${MPDL_INSTALL_BIN_DIR})
#install(FILES my-consolidated-include.hpp DESTINATION ${MPDL_INSTALL_INCLUDE_DIR})
