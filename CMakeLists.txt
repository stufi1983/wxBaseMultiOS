# Specify the minimum version.
cmake_minimum_required(VERSION 3.7)

project(WxBase)

# Add sources.
  set(
    PROG_SRCS
    src/main.cpp
    src/rc.rc
  )


IF (WIN32)

  # Specify the project name.
  # project(WxBase-win32)
  set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/win_x64)

  # set stuff for windows
  set(CMAKE_CXX_STANDARD 20)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)

 
  include(FetchContent)
  set(wxBUILD_SHARED OFF)

  message(WARNING "Fetching wxWidgets from git, this may take a long time...")
  message(STATUS "Fetching wxWidgets...")

  FetchContent_Declare(
    wxWidgets
    GIT_REPOSITORY https://github.com/wxWidgets/wxWidgets.git
    GIT_SHALLOW ON
  )
  FetchContent_MakeAvailable(wxWidgets)

  # Specify what is needed to create the main target.
  # the WIN32 is needed for Windows in order for it to look for WinMain
  # instead of the main function. This is ignored on other systems,
  # so it works on all platforms

  add_executable(${PROJECT_NAME} WIN32 ${PROG_SRCS})

  # Include the wxWidgets use file to initialize various settings.
  # include(wxWidgets)

  target_link_libraries(${PROJECT_NAME} PRIVATE wxcore wxnet)

  ELSE()
  # set stuff for other systems

  if(APPLE) #apple OS
    set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/mac)
    add_executable(${PROJECT_NAME} MACOSX_BUNDLE ${PROG_SRCS})
    set_target_properties(${PROJECT_NAME} PROPERTIES MACOSX_BUNDLE_INFO_PLIST ${CMAKE_CURRENT_SOURCE_DIR}/Info.plist)

  else() # Linux OS
    set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/linux)
    add_executable(${PROJECT_NAME} ${PROG_SRCS})

  endif() # Apple and Linux

    find_package(wxWidgets COMPONENTS core base xrc REQUIRED)
    include(${wxWidgets_USE_FILE})
    target_link_libraries(${PROJECT_NAME} ${wxWidgets_LIBRARIES})
ENDIF()

#all OS  
install (TARGETS ${PROJECT_NAME} RUNTIME DESTINATION bin)
