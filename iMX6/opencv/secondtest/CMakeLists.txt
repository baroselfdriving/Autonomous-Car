cmake_minimum_required(VERSION 2.8)
project(Capture)
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)


find_package( OpenCV REQUIRED )
add_definitions(-std=c++11)
include_directories( ../videoinput)

add_executable( capture_Rasp capture_Rasp.cpp ../videoinput/Signs.cpp ../videoinput/TrafficLights.cpp ../videoinput/line_detection.cpp)
add_executable( capture_iMX6 capture_i.MX6.cpp client.cpp uart.cpp communication.cpp ../videoinput/line_detection.cpp)
#add_executable( client client.cpp)
target_link_libraries( capture_iMX6 ${OpenCV_LIBS} Threads::Threads )
target_link_libraries( capture_Rasp ${OpenCV_LIBS} Threads::Threads )
#target_link_libraries( Capture1 ${OpenCV_LIBS} )
set(CMAKE_BUILD_TYPE Release)