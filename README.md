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
Binary file is available in the bin folder

## Windows
### Build
#### 1.  Using CMake (MSVC) - Recomended
Terminal -> run task -> Search for Kits, configure and build
This method will fetch wxWidgets from git, it may take a few hours
##### CMake Result
Binary is in *bin/windows64* for debug and release

#### 2. Using Task (MINGW)
Assume has wxWidgets is already installed. build wxWidget, install and set directory in set wxWidget_dir in setting.json
> "wxWidget_dir": "C:\\Program Files (x86)\\wxWidgets"

Choose Terminal menu -> run task -> Windows MinGW Build (or Windows MinGW Release)

##### Using Task Result
Binary is in *bin/win_x64/debug* for debug build. Or in *bin/win_x64/release* for release build.

## MacOS
### Preparation
Install brew, follow at https://brew.sh
in terminal:
> brew config

if it said
> zsh: command not found: brew

so, install brew by
>/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Update brew if it's already installed
>brew update
>brew doctor

Instal wxmac and check installation version
> brew install cmake
> brew install wxmac
> wx-configure --version

Install xcode (optional)
>brew install mas
>mas search xcode

Copy the id, which is 497799835, then install it using the id:
>mas install 497799835

### Set CMake path in VSCode
set cmake path to VSCode if not already in setting.json (Mac only)
> "cmake.cmakePath": "/usr/local/bin/cmake"

or edit CMake Tools extension settings

### Build using CMake
cmd + P run: Search for Kits, configure, build

### Result
Binary file is available in the *build/mac* folder