# The Copy & Swap Idiom

The copy & swap idiom allows you to implement assignment operators and even the move constructor using a swap operation.
```cpp
void swap(T& a, T& b) † noexcept †† {
    using std::swap; ††† // necessary
    swap(a.x, b.x);
    swap(a.y, b.y);
    // swap every member ...
}
T& T::operator=(T other) noexcept †† {
    // identical impl. for move-assignment
    swap(*this, other);
    return *this;
}
T::T(T&& other) noexcept †† { // optional
    // default-construct, then swap
    swap(*this, other);
}
```
**†** `swap` is often implemented as a [hidden friend](https://stackoverflow.com/q/56795676/5740428)  
**††** these operations are almost always **[noexcept](https://en.cppreference.com/w/cpp/language/noexcept_spec)**,
but there are rare exceptions
(e.g. **[std::list](https://en.cppreference.com/w/cpp/container/list/list)**)  
**†††** Because of [argument-dependent lookup (ADL)](https://en.cppreference.com/w/cpp/language/adl),
overloaded `swap` functions may be called instead of
**[std::swap](https://en.cppreference.com/w/cpp/algorithm/swap)**, which is used as a fallback.

## Pro & Contra
✅ simple implementation of assignments (and move constructor)  
✅ well-defined self-assignment  
✅ **[noexcept](https://en.cppreference.com/w/cpp/language/noexcept_spec)** copy/move assignment
if [std::is_nothrow_swappable<T>](https://en.cppreference.com/w/cpp/types/is_swappable)  
❌ copying always takes place, even for self-assignment  
❌ must implement custom `swap` instead of using `std::swap`

## See Also
<:stackoverflow:874353689031233606>
[What is the copy-and-swap idiom?](https://stackoverflow.com/a/3279550/5740428) (must read!)
