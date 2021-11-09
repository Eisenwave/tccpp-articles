# What are the different casts in c++

##C-style cast  
- Used to perform implicit or explicit type conversions between types  

```c++
(unsigned int) int_var;
```

##static_cast  
- Used to perform implicit or explicit type conversions between types  

```c++
static_cast<unsigned int>(int_var);
```

##reinterpret_cast  
- Converts type by reinterpreting the bits of the type

```c++
reinterpret_cast<int*>(nullptr);
```

##const_cast  
- Used to convert normal type to const type

```c++
const_cast<const int>(int_var);
```

##dynamic_cast  
- Used to either downcast or upcast a class with atleast one virtual method  

```c++
dynamic_cast<derived*>(base_ptr);
```

### Also See  
**[C-style cast](https://en.cppreference.com/w/cpp/language/explicit_cast)**  
**[static_cast](https://en.cppreference.com/w/cpp/language/static_cast)**  
**[reinterpret_cast](https://en.cppreference.com/w/cpp/language/reinterpret_cast)**  
**[const_cast](https://en.cppreference.com/w/cpp/language/const_cast)**  
**[dynamic_cast](https://en.cppreference.com/w/cpp/language/dynamic_cast)**  

**[Microsoft's article on casts](https://docs.microsoft.com/en-us/cpp/cpp/type-conversions-and-type-safety-modern-cpp)**

?creditFooter 379250891838193667
