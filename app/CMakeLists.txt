cmake_minimum_required(VERSION 3.4.1)

#源码树的顶层路径。
set(distribution_DIR ${CMAKE_SOURCE_DIR}src/main/jniLibs)
add_library(avcodec-57
            SHARED
            IMPORTED)
set_target_properties( avcodec-57
                       PROPERTIES IMPORTED_LOCATION
                        ../../../../src/main/jniLibs/armeabi/libavcodec-57.so )

add_library(
            avfilter-6
            SHARED
            IMPORTED)
set_target_properties( avfilter-6
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../src/main/jniLibs/armeabi/libavfilter-6.so )

add_library(
            avformat-57
            SHARED
            IMPORTED)
set_target_properties( avformat-57
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../src/main/jniLibs/armeabi/libavformat-57.so )

add_library(
            avutil-55
            SHARED
            IMPORTED)
set_target_properties( avutil-55
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../src/main/jniLibs/armeabi/libavutil-55.so )

add_library(
            swresample-2
            SHARED
            IMPORTED)
set_target_properties( swresample-2
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../src/main/jniLibs/armeabi/libswresample-2.so )

add_library(
            swscale-4
            SHARED
            IMPORTED)
set_target_properties( swscale-4
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../src/main/jniLibs/armeabi/libswscale-4.so )
add_library( avdevice-57
             SHARED
             IMPORTED)
set_target_properties( avdevice-57
                       PROPERTIES IMPORTED_LOCATION
                      ../../../../src/main/jniLibs/armeabi/libavdevice-57.so )

#支持-std=gnu++11
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11")


add_library( VideoPlayer
             SHARED
             src/main/cpp/VideoPlayer.cpp)

include_directories(src/main/cpp/include)

find_library(log-lib log )


target_link_libraries( # Specifies the target library.
                      VideoPlayer android avcodec-57 avfilter-6 avformat-57 avutil-55 swresample-2 swscale-4 avdevice-57
                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib} )
