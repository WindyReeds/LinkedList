cmake_minimum_required(VERSION 4.3)
project(A3)

set(CMAKE_CXX_STANDARD 20)

add_executable(A3 main.cpp
        Node.h
        List.h
        ArrayList.h
        LinkedList.h
        Data.h)
