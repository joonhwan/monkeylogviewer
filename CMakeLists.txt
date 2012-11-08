cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(monkeyLogViewer)

# Set up the environment
find_package(Qt4 REQUIRED)

include_directories(${CMAKE_CURRENT_BINARY_DIR})

if(WIN32)
set(QT_USE_QTMAIN ON)
endif()
set(QT_USE_QTNETWORK ON)
include(${QT_USE_FILE})

set(sources
  Source/main.cpp
  Source/MainWindow/MainWindow.cpp
  Source/MainWindow/StatusBar.cpp
  Source/MainWindow/MenuBar.cpp
  Source/MainWindow/TabWidget.cpp
  Source/MainWindow/TabBar.cpp
  Source/Setting/INIManager.cpp
  Source/Utils/LoadingWidget.cpp
  Source/FileLoader/FileLoadManager.cpp
  Source/FileLoader/FileReader.cpp
  Source/LogViewer/LogViewerManager.cpp
  Source/LogViewer/LogViewer.cpp
  Source/Option/OptionDialog.cpp
  Source/Option/FontSetupPage.cpp
  Source/Option/HighlightSetupPage.cpp
  Source/Keyword/KeywordHighlighter.cpp
  Source/Keyword/KeywordButtonGroup.cpp
  Source/Keyword/SearchLineEdit.cpp
  Source/MainWindow/AboutDialog.cpp
  Source/MainWindow/RecentFilesMenu.cpp
  Source/MainWindow/GotoLineDialog.cpp
  Source/Http/Http.cpp
  Source/Utils/Updater.cpp
  Source/Utils/ProgressDialog.cpp   
  Source/MainWindow/WindowsMenu.cpp
  Source/Keyword/HighlightingResult.cpp
  Source/DockWidget/DockWidget.cpp
  Source/DockWidget/FileBrowser/FileBrowser.cpp
  Source/DockWidget/ResultView/ResultView.cpp
  Source/DockWidget/ChartView/ChartView.cpp
  Source/Keyword/Chart.cpp
  Source/Utils/LoadingPopup.cpp
  )

set(moc_header
  Source/DockWidget/ChartView/ChartView.h
  Source/DockWidget/DockWidget.h
  Source/DockWidget/FileBrowser/FileBrowser.h
  Source/DockWidget/ResultView/ResultView.h
  Source/FileLoader/FileLoadManager.h
  Source/FileLoader/FileReader.h
  Source/Http/Http.h
  Source/Keyword/Chart.h
  Source/Keyword/HighlightingResult.h
  Source/Keyword/KeywordButtonGroup.h
  Source/Keyword/KeywordHighlighter.h
  Source/Keyword/SearchLineEdit.h
  Source/LogViewer/LogViewer.h
  Source/LogViewer/LogViewerManager.h
  Source/MainWindow/GotoLineDialog.h
  Source/MainWindow/MainWindow.h
  Source/MainWindow/MenuBar.h
  Source/MainWindow/RecentFilesMenu.h
  Source/MainWindow/StatusBar.h
  Source/MainWindow/TabBar.h
  Source/MainWindow/TabWidget.h
  Source/MainWindow/WindowsMenu.h
  Source/Option/FontSetupPage.h
  Source/Option/HighlightSetupPage.h
  Source/Option/OptionDialog.h
  Source/Setting/INIManager.h
  Source/Utils/ProgressDialog.h
  Source/Utils/Updater.h
  )

set(header
  Source/Config.h
  Source/Utils/LoadingWidget.h
  Source/TypeDef.h
  Source/LogViewer/LineNumberArea.h
  Source/MainWindow/AboutDialog.h
  Source/Utils/LoadingPopup.h
  )

set(forms
  )

set(resources
  qresource.qrc
  )

qt4_wrap_cpp(moc_generated ${moc_header})
qt4_wrap_ui(forms_generated ${forms})
qt4_add_resources(rc_generated ${resources})

include_directories(
  ${CMAKE_SOURCE_DIR}
  )

add_executable(${PROJECT_NAME} WIN32 MACOSX_BUNDLE
  ${sources}
  ${header}
  ${moc_header}
  ${form}
  ${resource}
  ${moc_generated}
  ${forms_generated}
  ${rc_generated}
  monkeyLogViewer.rc
  )

target_link_libraries(${PROJECT_NAME}
  ${QT_LIBRARIES}
  )
