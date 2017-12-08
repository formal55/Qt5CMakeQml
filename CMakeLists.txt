project(QtQmlCmake)
cmake_minimum_required(VERSION 3.0.2)

find_package(Qt5 REQUIRED
    Core
    Quick
    Qml
    Gui
)

include(${CMAKE_SOURCE_DIR}/qt_cmake_plugin/QtCommon.cmake REQUIRED)
FILE(GLOB_RECURSE QML_FILES "${CMAKE_SOURCE_DIR}/*.qml")
add_custom_target(qml_files SOURCES ${QML_FILES})

# Set additional project information
set(COMPANY "Toyota")
set(COPYRIGHT "Copyright (c) 2017 Toyota Liu. All rights reserved.")
set(IDENTIFIER "com.toyota.Example")

add_project_meta(META_FILES_TO_INCLUDE)

add_executable(${PROJECT_NAME} ${OS_BUNDLE} main.cpp ${META_FILES_TO_INCLUDE} ${CMAKE_SOURCE_DIR}/qml.qrc)
qt5_use_modules(${PROJECT_NAME} Core Gui Qml Quick)



