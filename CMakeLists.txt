cmake_minimum_required(VERSION 3.0.0)

project(CameraPose)
set(TARGET pose)

set(CMAKE_CXX_FLAGS "${CMKE_CXX_FLAGS} -std=c++11")

find_package(OpenCV 4.3.0 REQUIRED)
find_package(PkgConfig REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS}
                    ${CMAKE_BINARY_DIR} # this is the build dir, where the generated version.h file is located
                    ${PROJECT_SOURCE_DIR}/src        
                    )       

file(GLOB_RECURSE SOURCES "src/*.cpp")

add_executable(${TARGET} ${SOURCES})

target_link_libraries(${TARGET}
                      ${OpenCV_LIBS}
                      )
