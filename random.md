# Generating Random Numbers in C++

The [<random>](https://en.cppreference.com/w/cpp/header/random)
header in C++ provides (pseudo-)random number generation (PRNG):
- *[UniformRandomBitGenerators](https://en.cppreference.com/w/cpp/named_req/UniformRandomBitGenerators)*
produce random bits (entropy)
- *[RandomNumberDistributions](https://en.cppreference.com/w/cpp/named_req/RandomNumberDistribution)*
use entropy to generate random numbers

These types are used via their overloaded call operators.
## Example: Printing Ten Random Dice Rolls
```cpp
#include <random>
#include <iostream>
int main() {
  std::random_device dev; // for seeding
  std::default_random_engine gen{dev()};
  std::uniform_int_distribution<int> dis{1, 6};
  for (int i = 0; i < 10; ++i)
    std::cout << dis(gen) << ' ';
}
```
## Possible Output (will be different each time)
```cpp
1 1 6 5 2 2 5 5 6 2
```

## Common Generators
?inline
- **[std::random_device](https://en.cppreference.com/w/cpp/numeric/random/random_device)**:
truly random
- **[std::default_random_engine](https://timsong-cpp.github.io/cppwp/n4868/rand.predef#lib:default_random_engine)**
- **[std::mt19937](https://timsong-cpp.github.io/cppwp/n4868/rand.predef#lib:mt19937)**:
popular default choice
  
## Common Distributions
?inline
- **[std::uniform_int_distribution](https://en.cppreference.com/w/cpp/numeric/random/uniform_int_distribution)**
- **[std::uniform_real_distribution](https://en.cppreference.com/w/cpp/numeric/random/uniform_real_distribution)**
- **[std::normal_distribution](https://en.cppreference.com/w/cpp/numeric/random/normal_distribution)**

## Also See
<:cppreference:875716540929015908>
[Pseudo-random number generation](https://en.cppreference.com/w/cpp/numeric/random)  
<:stackoverflow:874353689031233606>
[Generate random numbers using C++11 random library](https://stackoverflow.com/q/19665818/5740428)  
<:stackoverflow:874353689031233606>
[Why is the use of rand() considered bad?](https://stackoverflow.com/q/52869166/5740428)