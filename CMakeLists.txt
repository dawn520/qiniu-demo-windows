cmake_minimum_required(VERSION 3.9)
project(qiniu)

#Qt
set(QT_HOME "D:\\Qt\\5.10.0\\mingw53_32")     #对应的Qt的安装目录
set(CMAKE_PREFIX_PATH ${QT_HOME})
SET(PROJECT_ROOT ${CMAKE_CURRENT_SOURCE_DIR})
set(CMAKE_INCLUDE_CURRENT_DIR on)
set(CMAKE_AUTOMOC on)
set(CMAKE_AUTOUIC on)
set(CMAKE_AUTORCC on)

###这里根据Project的实际情况来添加需要的模块
find_package(Qt5 REQUIRED Core Widgets UiTools Xml Network Qml Quick)


set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        main.cpp
        mainwindow.cpp
        mainwindow.h zcx.cpp zcx.h)

#set(CMAKE_CXX_FLAGS_COVERAGE "${CMAKE_CXX_FLAGS_RELEASE} -fprofile-arcs -ftest-coverage")
#set_target_properties(Qt5::Core PROPERTIES MAP_IMPORTED_CONFIG_COVERAGE "RELEASE")

#Set_Target_Properties(${PROJECT_NAME} PROPERTIES LINK_FLAGS_RELEASE "/SUBSYSTEM:WINDOWS /ENTRY:mainCRTStartup")
#Set_Target_Properties(${PROJECT_NAME} PROPERTIES LINK_FLAGS_RELEASE "/SUBSYSTEM:WINDOWS /ENTRY:mainCRTStartup")
##Set some Win32 Specific Settings
IF(WIN32)
    SET(GUI_TYPE WIN32)
ENDIF(WIN32)
# Set some Apple MacOS Specific settings
IF (APPLE)
    SET(GUI_TYPE MACOSX_BUNDLE)
ENDIF (APPLE)

#这里需要注意，如果你的Projetc中包含了qrc文件，则必须要将该qrc文件也加进来
#add_executable(<name> [WIN32] [MACOSX_BUNDLE]
#        [EXCLUDE_FROM_ALL]
#        source1 source2 ... sourceN)

add_executable(qiniu WIN32 ${SOURCE_FILES})

target_link_libraries(qiniu Qt5::Core Qt5::Widgets Qt5::Gui Qt5::UiTools Qt5::Xml Qt5::Network Qt5::Qml Qt5::Quick)