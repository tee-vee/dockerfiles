cmake_minimum_required(VERSION 2.8)
project(OpenCvTest)

find_package( OpenCV REQUIRED )
add_executable( OpenCvTest OpenCvTest.cpp )
target_link_libraries( OpenCvTest ${OpenCV_LIBS} )
