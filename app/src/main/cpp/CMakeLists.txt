cmake_minimum_required(VERSION 3.10.2)

projects("myapplication")

set(ANDROID_OPENCV_COMPONENTS "opencv_java" CACGE STRING "")
message(STATUS "ANDROID_ABI=${ANDROID_ABI}")
find_package(OpenCV REQUIRED COMPONENTS ${ANDROID_OPENCV_COMPONENTS})

add_library( native-lib SHARED native-lib.cpp )

find_library( log-lib log )

target_link_libraries( native-lib ${log-lib} ${ANDROID_OPENCV_COMPONENTS})