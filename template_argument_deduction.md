# What Is Template Argument Deduction?

In certain cases, the compiler is able to deduce which template parameters
should be used for a template instantiation, without the code being explicit
about it.

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
print<std::string>("Hi");
```

The first two calls to `print` will instantiate the template as function whose
signatures are `template<> void print(const char* arg);` and
`template<> void print(int arg);`, because the compiler matches `T` to the
static type of the provided arguments (`"Hello"` and `42`).

The third call inhibits deduction by imposing `std::string` as `T` in the
template. The template is instantiated a thrid time with a different signature,
and an `std::string` is first constructed from `"Hi"` before a copy of it is
passed to the function.

There are cases where the compiler cannot deduce template parameters, in which
case the code is required to be explicit about it. This typically happens when
a template parameters appears only in the return type:

**Template function**
?inline
```cpp
template<typename T>
T* construct_from_int(int arg) {
    return new T(arg);
}
```

**Usage**
?inline
```cpp
auto foo = construct_from_int<Foo>(42);
//         ^ ok, returns a Foo*
// (Foo must be constructible from int)
auto bar = construct_from_int(45);
//         ^ error: could not deduce T
```

Template parameters can be partially deduced independently of each other:  

**Template function**
?inline
```cpp
template<typename T, typename ArgT>
T* construct_from_arg(ArgT arg) {
    return new T(arg);
}
```

**Usage**
?inline
```cpp
Foo* foo = construct_from_arg<Foo>(42);
//         ^ ok, T is Foo, ArgT is deduced to int
Bar* bar = construct_from_arg<Bar, Baz>(65);
//         ^ ok, T is Bar, ArgT is Baz
// A Baz instance will be constructed from 65,
// and Bar must be constructible from Bar
```
