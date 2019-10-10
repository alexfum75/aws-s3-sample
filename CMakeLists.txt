cmake_minimum_required(VERSION 3.5)

project(s3-sample)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${SSE_FLAGS} -march=native  -std=c++0x") 

#include_directories(/home/itam/aws-sdk-cpp /home/itam/aws-sdk-cpp/aws-cpp-sdk-core/include /home/itam/aws_deps/ /home/itam/aws-c-event-stream/cmake/)

set(aws-sdk-cpp_DIR $ENV{AWS_SDK_CPP_DIR})
#this will locate the aws sdk for c++ package so that we can use its targets
find_package(aws-sdk-cpp)

add_executable(s3-sample main.cpp)

#since we called find_package(), this will resolve all dependencies, header files, and cflags necessary
#to build and link your executable. 
target_link_libraries(s3-sample aws-cpp-sdk-s3 aws-cpp-sdk-core)

