cmake_minimum_required(VERSION 3.14)

# Set your project's name and version
project(SIMDString VERSION 1.0.0)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Define the static library
add_library(SIMDString STATIC
    SIMDString.cpp
    SIMDString.h
)

# Set the include directories for the library
target_include_directories(SIMDString PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:include>
)

# If you have any compile definitions or options you'd like to add:
target_compile_definitions(SIMDString PRIVATE SIMDSTRING_LIBRARY)
# target_compile_options(SIMDString PRIVATE some-option)

# Set the version for the library
set_target_properties(SIMDString PROPERTIES VERSION ${PROJECT_VERSION})

# Install rules
install(TARGETS SIMDString
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
    RUNTIME DESTINATION bin
)
install(FILES SIMDString.h DESTINATION include)

# If you're using CTest for your tests
#include(CTest)
#enable_testing()
# add_subdirectory(tests) # Uncomment if you have a 'tests' directory
