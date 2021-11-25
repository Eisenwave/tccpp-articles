# C vs. C++: Which Is Better, Faster, ...?

Neither language is better, neither language is faster.
There are good reasons for using both languages:

## Reasons To Use C
?inline
✅ relatively low-level language
✅ much simpler language (no classes, templates, ...)  
✅ portable to a wide variety of systems
✅ only does what you say
✅ easy to mix with other languages

## Reasons To Use C++
?inline
✅ lots of helpful abstractions (classes, templates, ...)  
✅ feature-rich language (function overloads, `constexpr`, ...)  
✅ extensive standard library
✅ stricter syntax
✅ RAII prevents resource leaks

## Which Is Faster?
Neither language is inherently faster than the other.
In modern compilers, the exact same optimizer is used for both languages.

C++ mostly benefits from its robust standard library, reducing naïve DIY algorithms and
boilerplate significantly. It also uses an *exponentially* more efficient string representation
than C.

However, C++ can also hide slow tasks (e.g. allocations, large copies, exceptions, and RTTI
lookups) behind seemingly innocent code, all of which would be obvious in C.
## Conclusion
Both languages can be equally fast, choose the right language for your job, and the language you
enjoy working in.