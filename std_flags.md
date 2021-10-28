# How Do I Change the C++ Standard I'm Using?

You can change your C++ standard using compiler flags or project settings.

**Note:** Depending on your compiler version, some standards may not be available. 
Updating to a newer compiler is recommended.

## GCC and clang
?inline
- `-std=c++98`
- `-std=c++11`
- **...**
- `-std=c++20`
- `-std=c++2b`  
(`2b` is working draft C++23)

## MSVC
?inline
- `/std:c++98`
- `/std:c++11`
- **...**
- `/std:c++20`
- `/std:c++latest`  
(`latest` is working draft C++23)

## Visual Studio
?inline
Project → <name> → Settings → C/C++ → Language →  C++ Language Standard

## CMake
```cmake
set_target_properties(my_target PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO)
```
Or globally, for all targets:
```cmake
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CSS_STANDARD_REQUIRED YES)
```