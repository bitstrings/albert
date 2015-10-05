#http://doc.qt.io/qt-5/cmake-manual.html
cmake_minimum_required(VERSION 2.8.11)

project(files)

SET(TARGET_VERSION_MAJOR 1)
SET(TARGET_VERSION_MINOR 0)

find_package(Qt5Widgets 5.1 REQUIRED)
find_package(Qt5Svg REQUIRED)

include_directories(
    ../../application/ #TODO replace by coreapi
    ../../shared
    ../../application/pluginsystem/extension
)

set(${PROJECT_NAME}_SRCS
    metadata.json

    extension.cpp
    configwidget.cpp

    file.cpp
    fileactions.h
    indexer.cpp
#    src/mimetypedialog.cpp
#    src/mimetypechooser.cpp
)

qt5_wrap_ui(${PROJECT_NAME}_UIS
    configwidget.ui
#    src/mimetypedialog.ui
#    src/mimetypechooser.ui
)

ADD_LIBRARY(${PROJECT_NAME} SHARED ${${PROJECT_NAME}_SRCS} ${${PROJECT_NAME}_UIS})
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE C)
target_link_libraries(${PROJECT_NAME} ${Qt5Widgets_LIBRARIES} )