# How To Write Safer C/C++ Code

C and C++ are very powerful languages, but you need to be careful when using them.
Here are some crucial practices:

## Compiler Warnings!!!
?inline
- `-Wall`
- `-Wpedantic`
- `-Wextra`  
for GCC and clang catch most common mistakes.

You can also use [clang-tidy](https://clang.llvm.org/extra/clang-tidy/),
[IntelliSense](https://code.visualstudio.com/docs/editor/intellisense),
and other diagnostics (often integrated into IDEs).

## No Unsafe Functions
?inline
`scanf("%s", str)`, `gets()`, and others can lead to mistakes like
[buffer overflows](https://en.wikipedia.org/wiki/Buffer_overflow).

Accessing arrays out of bounds can be caught in C++ by using `.at(x)` instead of `[x]` for some containers.

## Prefer Smart Pointers
?inline
Since C++11, prefer smart pointers like
**[std::unique_ptr](https://en.cppreference.com/w/cpp/memory/unique_ptr)** and
**[std::shared_ptr](https://en.cppreference.com/w/cpp/memory/shared_ptr)**
over `new` and `delete`.

Without smart pointers, it's easy to forget to `delete` (or to mess it up) and to leak memory.

## Tracking Down Crashes, Memory Issues, Undefined Behavior

If your program is crashing, and you don't know why, you can track down the issue using additional software:  
- **[debuggers](https://en.wikipedia.org/wiki/Debugger)**
let you progress step by step, see the call stack, stop upon crashing, etc.
- **[ASan](https://en.wikipedia.org/wiki/AddressSanitizer)** tracks down memory issues like use-after-free:  
`-fsanitize=address`
- **[Valgrind](https://valgrind.org/docs/manual/quick-start.html)** is a Linux program which tracks down memory issues,
but attaches externally to an already compiled program

## Also See

- `!howto gdb`
- [TCCPPCon#1: Debugging with GDB](https://www.youtube.com/watch?v=bSEW0BvMiGc)
- [How do I enable compiler warnings?](https://64.github.io/cpp-faq/enable-warnings/)