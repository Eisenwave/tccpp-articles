# What Are the File Types in C/C++

## Source Files: `.c|.cpp|.cxx|...`
?inline
- function definitions 
- global variable definitions
- anything used **only** in that file

Each file is compiled independently, and in parallel.
Don't `#include` them, but compile each.

## Header Files: `.h|.hpp|.tpp|...`
?inline
- forward-declarations/prototypes
- type declarations
- templates

Headers are `#include`d into other source/header files.
You will need [include guards](https://64.github.io/cpp-faq/include-guards-pragma-once/) to prevent
[redefinition errors](https://stackoverflow.com/q/3746484/5740428).

## Translation Units and Lesser Known File Extensions

Each source file becomes a *translation unit* during
[translation](https://en.cppreference.com/w/cpp/language/translation_phases)
(expanding macros, remapping unicode characters, etc.) 

Sometimes `.ipp` or `.tpp` for C++ are used for internal headers with function definitions.

## Also See
?inline
📄 [How do header and source files in C work?](https://stackoverflow.com/q/5904530/5740428)  
📄 [What are 'Include Guards' and #pragma once?](https://64.github.io/cpp-faq/include-guards-pragma-once/)
  
## Common Errors
?inline
⛔ [Redefinition of ... (compiler)](https://stackoverflow.com/q/3746484/5740428)  
⛔ [Multiple definition of ... (linker)](https://stackoverflow.com/q/17764661/5740428)  
⛔ [Splitting templates into source/header](https://stackoverflow.com/q/1724036/5740428)