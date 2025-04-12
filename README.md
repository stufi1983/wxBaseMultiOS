# Welcome to wxWidget Multi OS VSCode

Install VSCode and C/C++ Extensioin Pack.  

## Linux
### Preparation
install:
> sudo apt-get install build-essential gdb ninja-build
> sudo apt-get install libwxgtk3.*-dev wx3.*-headers
### Build using CMake
Search for Kits, configure and build
### Result
Binary file is available in the build folder

## Windows
### Preparation
Nothing
### Build
#### Using CMake (MSVC) - Recomended
Terminal -> run task -> Search for Kits, configure and build
This method will fetch wxWidgets from git, it may take a few hours
#### Using Task (MINGW)
Assume has wxWidgets is already installed. build wxWidget, install and set directory in set wxWidget_dir in setting.json
> "wxWidget_dir": "C:\\Program Files (x86)\\wxWidgets",
Terminal -> run task -> Windows MinGW Build (or Windows MinGW Release)

### Result
A. Using CMake, binary is in *bin/windows64/debug* for debug
B. Using Task, binary is in *bin/win_x64/debug* for debug build. Or in *bin/win_x64/release* for release build.

## Mac
### Preparation
Install brew, follow at https://brew.sh

Instal wxmac and check installation version
> brew install wxmac
> wx-configure --version

set cmake path to VScode if not already in setting.json (Mac only)
> "cmake.cmakePath": "/usr/local/bin/cmake"

or edit CMake Tools extension settings

### Build using CMake
Search for Kits, configure and build

### Result
Binary file is available in the *build/mac* folder