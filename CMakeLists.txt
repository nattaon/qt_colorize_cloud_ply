cmake_minimum_required (VERSION 2.6 FATAL_ERROR)

project      (pcl-colorize_cloud)
#find_package (Qt5 REQUIRED)
#find_package (VTK REQUIRED)
find_package (PCL 1.8.1 REQUIRED)

include_directories (${PCL_INCLUDE_DIRS})
link_directories    (${PCL_LIBRARY_DIRS})
add_definitions     (${PCL_DEFINITIONS})

find_package (VTK REQUIRED)
include(${VTK_USE_FILE})

set  (project_SOURCES main.cpp pclviewer.cpp)
set  (project_HEADERS pclviewer.h)
set  (project_FORMS   pclviewer.ui)
set  (VTK_LIBRARIES)

QT5_WRAP_CPP (project_HEADERS_MOC   ${project_HEADERS})
QT5_WRAP_UI  (project_FORMS_HEADERS ${project_FORMS})

#INCLUDE         (${QT_USE_FILE})
ADD_DEFINITIONS (${QT_DEFINITIONS})

ADD_EXECUTABLE  (colorize_cloud ${project_SOURCES}
                                ${project_FORMS_HEADERS}
                                ${project_HEADERS_MOC})

TARGET_LINK_LIBRARIES (colorize_cloud ${QT_LIBRARIES} ${PCL_LIBRARIES} ${VTK_LIBRARIES})
qt5_use_modules (colorize_cloud Widgets)

