# Branchless Operations in C and C++

In C and C++, the results of boolean operators like `==`, `<`, can be used as `1` or `0` in arithmetic.
For example, `a == b` results in `1` if a and b are equal, otherwise `0`.

## Conditional Increment
?inline
```cpp
if (condition) a++;
// is equivalent to
a += condition;
```

## Conditional Addition
?inline
```cpp
if (condition) a += b;
// is equivalent to
a += condition * b;
```

## Comparison and Signum (results in -1, 0, or 1)
```cpp
int cmp(int a, int b) {
    return (a > b) - (a < b);
}
int sgn(int a) {
    return (a > 0) - (a < 0); // cmp(a, 0)
}
```

## Discussion
There are many more examples where these branchless operations are useful.
They can sometimes be more efficient than using an if-statement, but often,
modern compilers transform code into these branchless versions automatically, and there is no difference.

⚠️ **Keep readability in mind; others may find branchless code to be unintuitive and unreadable.**

## See Also
- [Creel - Branchless Programming](https://www.youtube.com/watch?v=bVJ-mWWL7cE)
- [How can I make branchless code?](https://stackoverflow.com/q/32107088/5740428)