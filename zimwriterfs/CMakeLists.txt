cmake_minimum_required(VERSION 3.4)
project(zimwriterfs)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(GUMBO_SOURCE_FILES
    gumbo/attribute.c
    gumbo/attribute.h
    gumbo/char_ref.c
    gumbo/char_ref.h
    gumbo/error.c
    gumbo/error.h
    gumbo/gumbo.h
    gumbo/insertion_mode.h
    gumbo/parser.c
    gumbo/parser.h
    gumbo/string_buffer.c
    gumbo/string_buffer.h
    gumbo/string_piece.c
    gumbo/string_piece.h
    gumbo/tag.c
    gumbo/token_type.h
    gumbo/tokenizer.c
    gumbo/tokenizer.h
    gumbo/tokenizer_states.h
    gumbo/utf8.c
    gumbo/utf8.h
    gumbo/util.c
    gumbo/util.h
    gumbo/vector.c
    gumbo/vector.h)

set(SOURCE_FILES
    ${GUMBO_SOURCE_FILES}
    zimwriterfs.cpp)

add_executable(zimwriterfs ${SOURCE_FILES})

find_package(Threads REQUIRED)
find_package(ZLIB REQUIRED)

include_directories(${ZLIB_INCLUDE_DIRS})

target_link_libraries(zimwriterfs zim)
target_link_libraries(zimwriterfs ${CMAKE_THREAD_LIBS_INIT})
target_link_libraries(zimwriterfs magic)
target_link_libraries(zimwriterfs ${ZLIB_LIBRARIES})
