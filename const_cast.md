# const_cast conversion

const_cast is an explicit cast operator that is mainly used to remove (or add) constness from/to a pointer or reference.
Before explaining const_cast, we first need to learn about top-level and low-level constness.

## Top level const
The top level const qualifier affects the object itself. This means that the object itself is immutable.
?inline
- For variables, the const-qualifier is always top-const;
- For pointers, a top-level const makes the pointer itself immutable (so you can't reassign a new address to it).
- The top-level const for pointers can be recognized easily since it is always after the asterisk.
- For references, there is no need to add a top-level const: they are always qualified with a top-level const, since a reference itself
can never be mutated.

```cpp
const int x = 4; // const for fundamental types is always top-level const
int* const my_pointer = /* ... */; // top level const - the pointer itself is const and cannot be reassigned
```

## Low level const
The low level const, unlike the top-one, does not affect the object itself. 
This type of const is only useful when working with references and pointers: a low level const makes it impossible for
a pointer or reference to mutate the object that they are pointing to or referencing.

```cpp
int not_const_variable = 5; // Note: this variable is not const
const int* pointer = &not_const_variable; // Low level const - the object pointed to is considered const
const int& reference = not_const_variable; // Low level const
```

In C++, a pointer can have both top level and low level constness at the same time.

const_cast is only able to remove or add the low-level constness, and never the top-level one (because otherwise we would break
the mutability of the object).

## Examples
- Remove constness:
```cpp
int main() {
    const int i = 0;
    const int* const pointer = &i;
    int* x = const_cast<int*>(pointer); // Remove low-level const from         
    // pointer -- valid
    *const_cast<int*>(pointer) = 2000; // No compile time error, but undefined 
    // behavior: we cannot mutate the object x points to, because it
    // has a top level const qualifier
}
```
 
- Add constness:
 ```cpp
 int main() {
    int i = 0;
    int* pointer = &i;
    *const_cast<const int*>(pointer) = 5; // Doesn't compile
    // because a low level const qualifier has been added!
}
```

## const_cast might be dangerous to use
Unless you have a very good reason to, you should avoid const_cast when possible. That's because it can easily lead
to undefined behavior, and also because it's very easy to break the const-best practices when using it.

## Also See
To learn about all the rules related to const_cast, visit
[cppreference: const_cast](https://en.cppreference.com/w/cpp/language/const_cast)
