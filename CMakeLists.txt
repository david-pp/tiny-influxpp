cmake_minimum_required(VERSION 3.2)
project(clion)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -g -Wno-deprecated-declarations")

include_directories(/usr/local/include)
link_directories(/usr/local/lib)

add_executable(example_influxdb example_influxdb.cpp InfluxDB.cpp InfluxDB.h)
target_link_libraries(example_influxdb curl)