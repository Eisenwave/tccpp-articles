# Constraining Templates in C++

By default, templates accept *any* argument, but this is often not desirable.
For instance, a `sqr(x)` function that computes `x²` only makes sense for numeric types.

**[Concepts](https://en.cppreference.com/w/cpp/language/constraints#Concepts)** (since C++20)  
Concepts don't constrain anything on their own, but are often used in constraints.
They often use a [requires expression](https://en.cppreference.com/w/cpp/language/constraints#Requires_expressions).
```cpp
template <typename T>
concept numeric = std::is_numeric_v<T>;
```

**[Type Constraints](https://en.cppreference.com/w/cpp/language/constraints#Constraints)** (since C++20)
```cpp
template <numeric T>
T sqr(T x);
```

**[Abbreviated Function Templates](https://en.cppreference.com/w/cpp/language/function_template#Abbreviated_function_template)** (since C++20)
This declaration also uses [deduced return types](https://en.cppreference.com/w/cpp/language/auto) (since C++14).
```cpp
auto sqr(numeric auto x);
```

**[Requires clauses](https://en.cppreference.com/w/cpp/language/constraints#Requires_clauses)** (since C++20)
```cpp
template <typename T>
requires numeric<T>
T sqr(T x);
```

**[std::enable_if](https://en.cppreference.com/w/cpp/types/enable_if)** (since C++11),
**[std::enable_if_t](https://en.cppreference.com/w/cpp/types/enable_if#Helper_types)** (since C++14)
```cpp
template <typename T>
auto sqr(T x) ->
  std::enable_if_t<std::is_numeric_v<T>, T>;
```

**[SFINAE in general](https://en.cppreference.com/w/cpp/language/sfinae)** (since C++98),
**[decltype](https://en.cppreference.com/w/cpp/language/decltype)** (since C++11)
```cpp
template <typename T>
auto sqr(T x) -> decltype(x * x);
```