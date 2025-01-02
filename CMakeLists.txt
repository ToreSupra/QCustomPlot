cmake_minimum_required(VERSION 3.28)

project (
	QCustomPlot
	VERSION 2.1.1
    LANGUAGES CXX
	HOMEPAGE_URL https://github.com/ToreSupra/QCustomPlot
)

find_package(
    Qt6
    COMPONENTS
        Core
        Gui
        Widgets
        PrintSupport
)

set(TARGET_STATIC "qcustomplot-static")

add_library(${TARGET_STATIC} STATIC)

target_compile_features(
    ${TARGET_STATIC}
    PUBLIC
        cxx_std_20
)

target_sources(
    ${TARGET_STATIC}
    PUBLIC
    FILE_SET
        HEADERS
        BASE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}
        FILES
            qcustomplot.h

    PRIVATE
        qcustomplot.cpp
)

target_link_libraries(
    ${TARGET_STATIC}
    PUBLIC
        Qt::Core
		Qt::Gui
		Qt::Widgets
		Qt::PrintSupport
)