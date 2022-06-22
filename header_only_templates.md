# Why must templates be defined in headers?

Template functions and classes are not real entities until they are
_instantiated_, which happens when a piece code uses the template with template
arguments: the compiler replaces the template parameters with the provided
arguments, and derives the generic code into specific code that uses those
arguments, thereby creating an entirely new function (or class).  

For this code derivation to happen, the code needs to be available in any
translation unit that attempts to use the template. This means that the generic
code must be part of the header where the template is declared, and thus also
defined.  

## Example

**Template function**
?inline
```cpp
template<typename T>
void print(T arg) {
    std::cout << arg << ' ';
}
```

**Usage**
?inline
```cpp
print("Hello");
print(42);
```

Upon reaching the first call to `print`, the compiler will use the template
definition to instantiate it as a new function whose signature is
`template<> void print(const char* arg);`. The second call to `print` has the
template instantiated as `template<> void print(int arg);`. The compiler
instantiates the template with those specific types thanks to a mechanism called
_template argument deduction_.

**Output:**
```
Hello 42 
```

?creditFooter 196563327973982208
