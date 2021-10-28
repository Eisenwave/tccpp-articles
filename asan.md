# How To Use Sanitizers

Sanitizers are tools which generate additional code in your program that can catch many common programming mistakes,
such as:
- [accessing arrays out of bounds](https://cwe.mitre.org/data/definitions/125.html)
- [signed integer overflows](https://cwe.mitre.org/data/definitions/190.html)
- [race conditions](https://cwe.mitre.org/data/definitions/362.html)

## General Advice

Not all sanitizers can be combined, but when they can, use e.g.:  
`-fsanitize=address,undefined` to combine them.
Always compile with debug info to get line numbers, variable names, etc.

## GCC 4.8+
?inline
- **[-fsanitize=address](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html#:~:text=-fsanitize%3Daddress)**
- **[-fsanitize=undefined](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html#:~:text=-fsanitize%3Dundefined)**
- **[-fsanitize=thread](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html#:~:text=ThreadSanitizer)**
- **-g** for debug info  

## clang 3.1+
?inline
- **[-fsanitize=address](https://clang.llvm.org/docs/AddressSanitizer.html)**
- **[-fsanitize=undefined](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html)**
- **[-fsanitize=thread](https://clang.llvm.org/docs/ThreadSanitizer.html)**
- **[-fsanitize=memory](https://clang.llvm.org/docs/MemorySanitizer.html)**
- **-g** for debug info  

## MSVC 19.27+ and VS 2019 16.9+
?inline
- **[-fsanitize=address](https://docs.microsoft.com/en-us/cpp/sanitizers/asan?view=msvc-160)**
- **-Zi** for debug info

## Sample Program
?inline
```cpp
int main(void) {
    int x;
    return x;
}
```

## `-fsanitize=memory -g` Output
?inline
> SUMMARY: MemorySanitizer: use-of-uninitialized-value /tmp/test.cpp:3:5 in main
> Exiting  
(`3:5` is line and column of `return`)

## Footer
?footer
Note: The sanitizer lists for GCC and clang are not exhaustive
