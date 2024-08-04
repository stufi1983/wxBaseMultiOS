# Specify the minimum version.
cmake_minimum_required(VERSION 3.7)

project(WxBase)

# Add sources.
set(
  PROG_SRCS
  src/main.cpp
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

  add_executable(${PROJECT_NAME} WIN32 ${PROG_SRCS} manifest.manifest)

  # Include the wxWidgets use file to initialize various settings.
  #include(wxWidgets)

  target_link_libraries(${PROJECT_NAME} PRIVATE wxcore wxnet)

  ELSE()
# set stuff for other systems

  if(APPLE)
    # project(WxBase-mac)
    set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/mac)
    # create bundle on apple compiles
    add_executable(main MACOSX_BUNDLE ${SRCS})

    # Set a custom plist file for the app bundle - needed for Mac OS Retina display
    set_target_properties(main PROPERTIES MACOSX_BUNDLE_INFO_PLIST ${CMAKE_CURRENT_SOURCE_DIR}/Info.plist)

  else()

    # project(WxBase-linux)
    set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/linux)

    # Request the required wxWidgets libs.
    find_package(wxWidgets COMPONENTS core base xrc REQUIRED)

    # Include the wxWidgets use file to initialize various settings.
    include(${wxWidgets_USE_FILE})


    # Specify what is needed to create the main target.
    add_executable(${PROJECT_NAME} ${PROG_SRCS})


    # Link required libraries to the executable
    target_link_libraries(${PROJECT_NAME} ${wxWidgets_LIBRARIES})
  endif()
ENDIF()
  
  # Specify how to install the binary.
  install (TARGETS ${PROJECT_NAME} RUNTIME DESTINATION bin)


