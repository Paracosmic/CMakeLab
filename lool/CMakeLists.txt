cmake_minimum_required(VERSION 3.8)

# set the project name
project(Tutorial VERSION 1.5 LANGUAGES CXX)

configure_file(test.h.in test.h)

#compile library

add_library(aalib INTERFACE common/aa.h)

target_include_directories(aalib INTERFACE  common)

target_compile_features(aalib INTERFACE  cxx_std_11)

set_target_properties(aalib PROPERTIES LINKER_LANGUAGE CXX)

set_target_properties(aalib PROPERTIES
         LIBRARY_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR})


# add the executable
add_executable(Tutorial ConsoleApplication2.cpp
)

target_link_libraries(Tutorial PUBLIC aalib)








