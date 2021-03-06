
cmake_minimum_required(VERSION 3.4.1)

file(GLOB my_source src/main/cpp/*.cpp src/main/cpp/*.c)

add_library( # Sets the name of the library.
             native-lib

             # Sets the library as a shared library.
             SHARED

             ${my_source} )

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

include_directories(libs/include)

set(DIR ../../../../libs)

add_library(avcodec-56
            SHARED
            IMPORTED)
set_target_properties(avcodec-56
                      PROPERTIES IMPORTED_LOCATION
                      ${DIR}/armeabi/libavcodec-56.so)

add_library(avdevice-56
            SHARED
            IMPORTED)
set_target_properties(avdevice-56
                      PROPERTIES IMPORTED_LOCATION
                      ${DIR}/armeabi/libavdevice-56.so)

add_library(avformat-56
            SHARED
            IMPORTED)
set_target_properties(avformat-56
                      PROPERTIES IMPORTED_LOCATION
                      ${DIR}/armeabi/libavformat-56.so)

add_library(avutil-54
            SHARED
            IMPORTED)
set_target_properties(avutil-54
                      PROPERTIES IMPORTED_LOCATION
                      ${DIR}/armeabi/libavutil-54.so)

add_library(postproc-53
            SHARED
            IMPORTED)
set_target_properties(postproc-53
                      PROPERTIES IMPORTED_LOCATION
                      ${DIR}/armeabi/libpostproc-53.so)

add_library(swresample-1
             SHARED
             IMPORTED)
set_target_properties(swresample-1
                       PROPERTIES IMPORTED_LOCATION
                       ${DIR}/armeabi/libswresample-1.so)

add_library(swscale-3
              SHARED
              IMPORTED)
set_target_properties(swscale-3
                        PROPERTIES IMPORTED_LOCATION
                        ${DIR}/armeabi/libswscale-3.so)

add_library(avfilter-5
              SHARED
              IMPORTED)
set_target_properties(avfilter-5
                        PROPERTIES IMPORTED_LOCATION
                        ${DIR}/armeabi/libavfilter-5.so)

target_link_libraries( native-lib
                       avcodec-56
                       avdevice-56
                       avformat-56
                       avutil-54
                       postproc-53
                       swresample-1
                       swscale-3
                       avfilter-5
                       ${log-lib}
                       android
                       OpenSLES )