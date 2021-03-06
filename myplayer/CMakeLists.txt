
cmake_minimum_required(VERSION 3.4.1)

include_directories(src/main/cpp/include)
include_directories(src/main/cpp/soundtouch/include)
include_directories(src/main/cpp/soundtouch/SoundTouch)

add_library( # Sets the name of the library.
             native-lib

             SHARED

             src/main/cpp/native-lib.cpp
              src/main/cpp/CjAudio.cpp
              src/main/cpp/CjVideo.cpp
              src/main/cpp/CjCallJava.cpp
              src/main/cpp/CjFFmpeg.cpp
              src/main/cpp/CjQueue.cpp
              src/main/cpp/CjPlaystatus.cpp
               src/main/cpp/CjPcmBean.cpp
                src/main/cpp/CjBufferQueue.cpp

              src/main/cpp/soundtouch/SoundTouch/AAFilter.cpp
              src/main/cpp/soundtouch/SoundTouch/FIFOSampleBuffer.cpp
              src/main/cpp/soundtouch/SoundTouch/FIRFilter.cpp
              src/main/cpp/soundtouch/SoundTouch/cpu_detect_x86.cpp
              src/main/cpp/soundtouch/SoundTouch/sse_optimized.cpp
              src/main/cpp/soundtouch/SoundTouch/RateTransposer.cpp
              src/main/cpp/soundtouch/SoundTouch/SoundTouch.cpp
              src/main/cpp/soundtouch/SoundTouch/InterpolateCubic.cpp
              src/main/cpp/soundtouch/SoundTouch/InterpolateLinear.cpp
              src/main/cpp/soundtouch/SoundTouch/InterpolateShannon.cpp
              src/main/cpp/soundtouch/SoundTouch/TDStretch.cpp
              src/main/cpp/soundtouch/SoundTouch/PeakFinder.cpp
              )

add_library( avcodec-58 SHARED IMPORTED)
set_target_properties( avcodec-58
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libavcodec-58.so)


add_library( avdevice-58 SHARED IMPORTED)
set_target_properties( avdevice-58
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libavdevice-58.so)


add_library( avfilter-7 SHARED IMPORTED)
set_target_properties( avfilter-7
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libavfilter-7.so)


add_library( avformat-58 SHARED IMPORTED)
set_target_properties( avformat-58
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libavformat-58.so)


add_library( avutil-56 SHARED IMPORTED)
set_target_properties( avutil-56
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libavutil-56.so)

add_library( postproc-55 SHARED IMPORTED)
set_target_properties( postproc-55
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libpostproc-55.so)

add_library( swresample-3 SHARED IMPORTED)
set_target_properties( swresample-3
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libswresample-3.so)


add_library( swscale-5 SHARED IMPORTED)
set_target_properties( swscale-5
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libswscale-5.so)


target_link_libraries( # Specifies the target library.
                       native-lib

                       avcodec-58
                       avdevice-58
                       avfilter-7
                       avformat-58
                       avutil-56
                       postproc-55
                       swresample-3
                       swscale-5

                       OpenSLES

                       # Links the target library to the log library
                       # included in the NDK.
                      log )