cmake_minimum_required(VERSION 3.9)
project(boost_server)

set(CMAKE_CXX_STANDARD 11)

set(Boost_USE_STATIC_LIBS OFF)
set(Boost_USE_MULTITHREADED ON)
set(Boost_USE_STATIC_RUNTIME OFF)

find_package(Boost COMPONENTS system filesystem coroutine REQUIRED)
include_directories(${Boost_INCLUDE_DIR})

set(SOURCE_FILES main.cpp server.cpp server.hpp request_parser.cpp request_parser.hpp request.hpp reply.cpp reply.hpp mime_types.hpp mime_types.cpp header.hpp file_handler.cpp file_handler.hpp)
add_executable(boost_server ${SOURCE_FILES})
TARGET_LINK_LIBRARIES(boost_server LINK_PUBLIC ${Boost_LIBRARIES})