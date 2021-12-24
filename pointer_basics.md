# Pointer Basics

A Pointer is a variable that can only hold memory addresses.

## Declaring Pointers:
Since pointers can only store addresses, we typically assign another varaible's address to it. We can do so with the adress of operator(&).

```cpp
int var1 = 50;
int* ptr1 = &var1;
```

## Accessing Values of Pointers:
Printing the value of the pointer itself will print the memory address it is pointing to. In order to access the value that it's pointing to we need to use the
dereference operator(*).

```cpp
std::cout << *ptr1 << "\n";
```

## See Also:
- [Introduction to pointers](https://www.learncpp.com/cpp-tutorial/introduction-to-pointers/)
- [Pointer declaration](https://en.cppreference.com/w/cpp/language/pointer)
- `!howto pointer`
