# The Copy & Swap Idiom

The copy & swap idiom allows you to implement assignment operators and even the move constructor using a swap operation.

## Copy Assignment
?inline
```cpp
T& T::operator=(
    T other)
{
    using std::swap;
    swap(*this, other);
    return *this;
}
```

## Move Assignment (Optional)
?inline
```cpp
T& T::operator=(
    T&& other)
{
    using std::swap;
    swap(*this, other);
    return *this;
}
```

## Explanation

Because of [argument-dependent lookup (ADL)](https://en.cppreference.com/w/cpp/language/adl),
our own `swap(T&, T&)` function may be called instead of
**[std::swap](https://en.cppreference.com/w/cpp/algorithm/swap)**.

✅ simple implementation of assignments (and move constructor)  
✅ well-defined self-assignment  
✅ **[noexcept](https://en.cppreference.com/w/cpp/language/noexcept)** copy/move assignment
if [std::is_nothrow_swappable<T>](https://en.cppreference.com/w/cpp/types/is_swappable)  
❌ copying always takes place, even for self-assignment

## See Also
<:stackoverflow:874353689031233606>
[What is the copy-and-swap idiom?](https://stackoverflow.com/a/3279550/5740428) (must read!)
