# What Is the Conditional Operator?

The [conditional operator](https://en.cppreference.com/w/cpp/language/operator_other#Conditional_operator),
(colloquially called _ternary operator_)
of the form `Condition ? T : F` evaluates `T` if the `Condition` is true, otherwise `F`.

The result of the whole expression is either the expression `T` or `F`.
This also means that `T` and `F` must have compatible types.

## Example

A classic use case for the conditional operator is the `min` function.
```cpp
int min(int a, int b) {
    return a < b ? a : b;
}
```

This function chooses `a` if `a` is lower than `b`, or `b` otherwise.

## Benefits Over If-Statements
?inline
- more concise code
- makes it easier to be `const`-correct

## Downsides
?inline
- can be hard to read, especially when nested and formatted poorly

?creditFooter 162964325823283200