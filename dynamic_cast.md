## dynamic_cast conversion
dynamic_cast is an explicit cast operator that is often used when working with inheritance hierarchies, to convert pointers
(and references) from the derived  class to the base class (upcasting) and the opposite (downcasting). 
This operator performs a run-time check to test whether the conversion can be done, that is, it returns a null pointer
if the conversion could not be applied. This also implies a little overhead when using this cast.

## Useful conversions
dynamic_cast is mostly used when we need to downcast a base class to its derived class. 
It is often important to check whether the cast was successful: we can simply test whether the pointer returned by 
dynamic_cast is nullptr, and if it is, the conversion did not work correctly.
```cpp
int main() {
    Base* base = new Derived;
    if (Derived* derived = dynamic_cast<Derived*>(base); derived != nullptr) /* Check that the conversion did not fail */ {
        derived->foo();
    }
    // Note: If base didn't point to a derived object, the if statement would never execute because derived would be null
    delete base;
}
```

## Notes
Downcasting can be applied through static_cast as well, but in that case no runtime check is performed.
Unless you can prove that the conversion will not fail, you should use dymamic_cast in that it's safer and might avoid
unwanted issues.


## Also See
To learn about all the rules related to dynamic_cast, visit
[cppreference: dynamic_cast](https://en.cppreference.com/w/cpp/language/dynamic_cast)
