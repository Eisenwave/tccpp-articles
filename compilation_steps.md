# How Is C/C++ Source Code Compiled?

\:hash: The **preprocessor** expands macros and copy-pastes the content of included files
at their point of inclusion. After being preprocessed, a source file no longer
contains preprocessor directives. The result is called a _translation unit_ (TU).

> :bulb: _The preprocessor merely does text replacement, it does not care about any aspect of C/C++._

:ce: The **compiler** turns instructions into machine code and enforces C/C++
syntax rules. In particular, anything that is used must be have been declared
beforehand. The compiler only needs to know that something **exists**, not how
it is _defined_.

> :bulb: _Headers are a convenient way to expose function declarations to the compiler. Function definitions can reside in another, separately compiled TU, allowing finer control over the compilation process._

As function definitions might be unavailable at this point, the compiler emits
dummy machine code for function calls. A final step must be performed to fix those.

:link: The **linker** takes all compiled TUs at once and patches the dummy calls
emitted by the compiler. For each of those, the linker finds the compiled
function and inserts an address to jump to when the call is performed.

> :bulb: _Errors stating `undefined reference` or `unresolved external symbol` are linker errors, and they occur when the linker is unable to find a definition within the TUs it was given._

The linker also packs all the compiled code into one of three file formats:
an executable, a static library, or a dynamic link library.