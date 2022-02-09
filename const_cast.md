## `const_cast` conversion
`const_cast` is an explicit cast operator that is mainly used to remove (or add) constness from/to a pointer or reference.
This operator can only remove or add the constness to **what a pointer (or reference) points to**, and *never* the constness of the object itself: otherwise, we would break the immutability of the object.

## Examples
- Remove constness:
```cpp
int main() {
    const int i = 0;
    const int* const pointer = &i;
    int* x = const_cast<int*>(pointer); // Remove const from         
    // what the pointer points to -- valid
    *const_cast<int*>(pointer) = 2000; // No compile time error, but undefined 
    // behavior: we cannot mutate the object x points to, because it is originally const!
}
```
- Add constness:
 ```cpp
 int main() {
    int i = 0;
    int* pointer = &i;
    *const_cast<const int*>(pointer) = 5; // Doesn't compile
    // since we added a const qualifier: we now cannot mutate this object's value!
}
```

## `const_cas`t might be dangerous to use
Unless you have a very good reason to, *you should avoid `const_cast`*. It can easily lead
to undefined behavior and it's very easy to break the constness-related best practices while using it.

## Also See
[cppreference: const_cast](https://en.cppreference.com/w/cpp/language/const_cast)
[how to use const_cast?](https://stackoverflow.com/questions/19554841/how-to-use-const-cast)
[is const_cast safe?](https://stackoverflow.com/questions/357600/is-const-cast-safe)
