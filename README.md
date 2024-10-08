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
### Build
#### Using CMake
Search for Kits, configure and build
This method will fetch wxWidgets from git, it may take a few hours
#### Using Task
Assume has wxWidgets is already installed. build wxWidget, install and set directory in set wxWidget_dir in setting.json
> "wxWidget_dir": "C:\\Program Files (x86)\\wxWidgets",

Terminal -> run task -> Windows MinGW Build (or Windows MinGW Release)

### Result
Using CMake, binary is in *build/win_x64*

When using Task, binary is in *build/win_x64/debug* for debug build. Or in */src/build/g++/release* (I have diificulty to move it into build/win_x64) 

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

# Readme.md Template

in progress
|                |ASCII                          |HTML                         |
|----------------|-------------------------------|-----------------------------|
|Single backticks|`'Isn't this fun?'`            |'Isn't this fun?'            |
|Quotes          |`"Isn't this fun?"`            |"Isn't this fun?"            |
|Dashes          |`-- is en-dash, --- is em-dash`|-- is en-dash, --- is em-dash|


## KaTeX Example

You can render LaTeX mathematical expressions using [KaTeX](https://khan.github.io/KaTeX/):

The *Gamma function* satisfying $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$ is via the Euler integral

$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$

> You can find more information about **LaTeX** mathematical expressions [here](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference).


## UML diagrams example

You can render UML diagrams using [Mermaid](https://mermaidjs.github.io/). For example, this will produce a sequence diagram:

```mermaid
sequenceDiagram
Alice ->> Bob: Hello Bob, how are you?
Bob-->>John: How about you John?
Bob--x Alice: I am good thanks!
Bob-x John: I am good thanks!
Note right of John: Bob thinks a long<br/>long time, so long<br/>that the text does<br/>not fit on a row.

Bob-->Alice: Checking with John...
Alice->John: Yes... John, how are you?
```

And this will produce a flow chart:

```mermaid
graph LR
A[Square Rect] -- Link text --> B((Circle))
A --> C(Round Rect)
B --> D{Rhombus}
C --> D
```
