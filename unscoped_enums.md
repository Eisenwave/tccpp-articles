# Unscoped Enums

General Syntax for unscoped enums:

enum enum_key enum_name: enumerator_type { };

- enum_key defines if the enum will be scoped or not.
- By defualt the enum_key is unscoped, and is not written.
- This means that the enum is visible to the entire scope it is defined in.

?inline
```
enum State {Engine_Failure, Inclement_Weather, Nominal};

std::underlying_type_t<State> user_input;
std::cin >> user_input;
        
State state;
switch (user_input) {
  case Engine_Failure:
    state = State(user_input);
    break;
  case Inclement_Weather:
    state = State(user_input);
    break;
  case Nominal:
    state = State(user_input);
    break;
  defualt:
    std::cout << "User input is not a valid state! \n";
}
```

In this Rocket Launch example the user enters an action to perform. The underlying data type of the enum is int, we type cast it to a specific enum using
std::underlying_type_t<enum>. We then use a switch statement to perform the action we want.

## See Also
- [Enumeration Declaration](https://en.cppreference.com/w/cpp/language/enum)
- [Enumerated Types](https://www.learncpp.com/cpp-tutorial/enumerated-types/)
