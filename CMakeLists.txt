cmake_minimum_required(VERSION 3.10)
project(httpparser LANGUAGES CXX)

# Declare a header-only interface library
add_library(httpparser INTERFACE)

# Set the include directories
target_include_directories(httpparser INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>
        $<INSTALL_INTERFACE:include>
)

# Set the C++ standard for consumers
target_compile_features(httpparser INTERFACE cxx_std_20)

# Optional: install rules for consumers who want to install this library
install(TARGETS httpparser EXPORT httpparserTargets)
install(DIRECTORY src/httpparser DESTINATION include)
