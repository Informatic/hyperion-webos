cmake_minimum_required(VERSION 3.6)
project(hyperion-webos VERSION 1.0 LANGUAGES C)

add_subdirectory(tv-native-apis)
add_subdirectory(flatccrt)

find_package(PkgConfig REQUIRED)

pkg_check_modules(EGL egl REQUIRED)
pkg_check_modules(GLESv2 glesv2 REQUIRED)

add_executable(hyperion-webos
    src/capture.c
    src/hyperion_client.c
 )
target_include_directories(hyperion-webos PRIVATE fbs)
target_link_libraries(hyperion-webos vt flatccrt pthread ${GLESv2_LIBRARIES} ${EGL_LIBRARIES})