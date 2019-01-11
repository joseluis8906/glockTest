cmake_minimum_required(VERSION 2.6)
project(GlockTest)

set(GlockTest_VERSION_MAJOR 1)
set(GlockTest_VERSION_MINOR 0)
set(LOCAL_LIB_DIR "/home/joseluis/.local/lib")
set(LOCAL_INCLUDE_DIR "/home/joseluis/.local/include/")

configure_file(
    "${PROJECT_SOURCE_DIR}/GlockTestConfig.h.in"
    "${PROJECT_BINARY_DIR}/GlockTestConfig.h"
)

include_directories("${PROJECT_BINARY_DIR}")

option(USE_GLOCK "Use glock library" ON)
if(USE_GLOCK) 
    include_directories("${LOCAL_INCLUDE_DIR}/Glock")
    link_directories("${LOCAL_LIB_DIR}")
    set(EXTRA_LIBS ${EXTRA_LIBS} Glock)
endif(USE_GLOCK)

add_executable(GlockTest Application.cpp)
target_link_libraries(GlockTest ${EXTRA_LIBS})