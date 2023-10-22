cmake_minimum_required(VERSION 3.22)


set(CMAKE_TOOLCHAIN_FILE "C:/vcpkg/scripts/buildsystems/vcpkg.cmake"
  CACHE STRING "Vcpkg toolchain file") #vcpkg使用默认安装在c盘根目录下，因为如果路径太深，vcpkg安装qt模块的时候可能会编译目录太深而导致失败

project(demo)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_SCAN_FOR_MODULES NO) #https://cmake.org/cmake/help/latest/variable/CMAKE_CXX_SCAN_FOR_MODULES.html 当前不使用cmake对c++20module的支持，所以关闭scan_modules

find_package(Qt6 CONFIG REQUIRED)

find_package(Qt6Core CONFIG REQUIRED)

find_package(Qt6Gui CONFIG REQUIRED)

find_package(Qt6OpenGL CONFIG REQUIRED)

find_package(Qt6OpenGLWidgets CONFIG REQUIRED)

find_package(Qt6Widgets CONFIG REQUIRED)

AUX_SOURCE_DIRECTORY(. A)

#set(PROJECT_UIS mainwindow.ui)

qt_standard_project_setup()

qt_add_executable(demo ${A})# ${PROJECT_UIS})

target_link_libraries(demo PRIVATE Qt::Core Qt6::Core Qt::CorePrivate Qt6::CorePrivate PRIVATE Qt::Gui Qt6::Gui Qt::GuiPrivate Qt6::GuiPrivate PRIVATE Qt::OpenGL Qt6::OpenGL Qt::OpenGLPrivate Qt6::OpenGLPrivate PRIVATE Qt::Widgets Qt6::Widgets Qt::WidgetsPrivate Qt6::WidgetsPrivate PRIVATE Qt::OpenGLWidgets Qt6::OpenGLWidgets Qt::OpenGLWidgetsPrivate Qt6::OpenGLWidgetsPrivate)