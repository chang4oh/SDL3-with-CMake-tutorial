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

## File Structure

```
ProjectRoot/
│
├── SDL/
│   └── (SDL source)
│
└── SDL CMake/
    ├── CMakeLists.txt
    └── hello.c
```
