## `dynamic_cast` conversion
`dynamic_cast` is an explicit cast operator that is often used when working with inheritance hierarchies, to convert pointers
(and references) from the derived  class to the base class (upcasting) and the opposite (downcasting). 
This operator performs a runtime check to test whether the conversion can be done: it returns a null pointer on failure. 
This implies a little overhead when using it.

## Useful conversions
`dynamic_cast` is mostly used when we need to downcast a base class to its derived class. 
It is important to check whether the cast was successful: we can test whether the pointer returned by 
`dynamic_cast` is nullptr, and if it is, the conversion failed.
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
You can downcast with `static_cast` too, but no runtime check is performed.
Unless you can prove that the conversion will not fail, use use dymamic_cast in that it's safer and will avoid
unwanted issues.


## See Also
- [cppreference: dynamic_cast](https://en.cppreference.com/w/cpp/language/dynamic_cast)
- [how to down_cast correctly](https://stackoverflow.com/questions/52556957/how-to-use-dynamic-cast-to-downcast-correctly)
- [is dynamic_cast considered bad design?](https://stackoverflow.com/questions/48612271/use-case-of-dynamic-cast)
