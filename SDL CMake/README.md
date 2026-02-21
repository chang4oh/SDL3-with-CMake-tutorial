# SDL CMake

CMakeLists.txt has been modified to follow file structure  
by replacing

```
add_subdirectory(vendored/SDL EXCLUDE_FROM_ALL)
```

with

```
add_subdirectory(../SDL SDL-build EXCLUDE_FROM_ALL)
```

instead of standalone add_exectuable, added to check WIN32 or else assumed linux  
although I am using windows, my terminal is WSL, terminal function as like WSL
technically just 'add_executable(hello src/hello.c)' is fine in this case.

```
if(WIN32)
    add_executable(hello WIN32 src/hello.c)
else()
    add_executable(hello src/hello.c)
endif()
```

## SDL Error

I am currently using WSL as terminal  
Platform: Linux-6.6...-WSL2

There is an error

```
SDL could not find X11 or Wayland development libraries
SDL will not be able to create windows
```

This is missing linux libraries problem
**note**: This took me hours for me to make it work  
because it's fairly new version and dependencies are not all in one install  
Solution is to install required packages

```
// for CMake Error... Couldn't find dependency package for XSCRNSAVER.
sudo apt install \
  libasound2-dev libpulse-dev libaudio-dev libjack-dev \
  libx11-dev libxext-dev libxcursor-dev libxinerama-dev \
  libxrandr-dev libxi-dev libxss-dev libxtst-dev \
  libxkbcommon-dev libdrm-dev libgbm-dev libusb-1.0-0-dev \
  libwayland-dev libdecor-0-dev
```

## CMake and Ninja

'rm -rf build' if needing to clear build
'rm -rf \*' to clear current directory

```
mkdir build
cd build
cmake -G Ninja ..
ninja
```

after that go back to /SDL CMake
and do

```
./build/hello
```

You will see the finished work!

## File Structure

```
SDL CMake # used to be vendored/SDL
├── include
├── src
│  └── hello.c
├── CMakeLists.txt
└── README.md
```
