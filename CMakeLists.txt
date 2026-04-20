cmake_minimum_required(VERSION 4.2)
project(limit_order_book)

set(CMAKE_CXX_STANDARD 20)

add_executable(limit_order_book main.cpp)

if(MSVC)
    target_compile_options(limit_order_book PRIVATE /W4 /permissive- /WX)
else()
    target_compile_options(limit_order_book PRIVATE
            -Wall -Wextra -Wpedantic
            -Wshadow -Wconversion -Wsign-conversion
            -Wnon-virtual-dtor -Wold-style-cast
            -Wcast-align -Wunused -Woverloaded-virtual
            -Wnull-dereference -Wdouble-promotion
            -Wformat=2
            -Werror)
endif()

