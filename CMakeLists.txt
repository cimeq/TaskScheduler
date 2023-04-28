cmake_minimum_required(VERSION 3.14)

project(TaskScheduler VERSION 3.7.0)
message(STATUS "${PROJECT_NAME} Version: ${PROJECT_VERSION}")

add_library(${PROJECT_NAME} INTERFACE)
add_library(GitHub::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_include_directories( ${PROJECT_NAME}
        INTERFACE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
        )
target_compile_features(${PROJECT_NAME} INTERFACE cxx_std_17)

get_target_property(_TARGET_TYPE ${PROJECT_NAME} TYPE)
if(_TARGET_TYPE STREQUAL "INTERFACE_LIBRARY")
    set_target_properties(${PROJECT_NAME} PROPERTIES INTERFACE_VERSION ${PROJECT_VERSION} )
else()
    set_target_properties(${PROJECT_NAME} PROPERTIES VERSION ${PROJECT_VERSION} )
endif()
