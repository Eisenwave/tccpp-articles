# What Are `undefined reference` Errors and Why Do I Get Them?

`undefined reference` errors happen during the final step of compilation. In
order to understand them, here follows a refresher on these steps.

## Preprocessing

Compilation only happens in source files, as header files mostly contain only
_declarations_. Header contents get copy-pasted by the **preprocessor** at their
point of inclusion in source files. The result of this operation, among
others, is called a _translation unit_ (TU), which the **compiler** can then
process individually.  

## Compilation

The compiler turns instructions into machine code. When it sees a function call,
it inserts machine code that will jump to the compiled function. The compiler
only needs to know that the function _exists_, which is what headers are
included for. The definition can reside in another TU, and need not be visible
to the compiler. A final step must be performed before function calls can happen
at runtime.  

## Linking

When all TUs are compiled, the **linker** takes them all in and matches
the function calls to the compiled definitions of these functions.
`undefined reference` errors are the linker being unable to find some
definitions within the provided TUs.  
