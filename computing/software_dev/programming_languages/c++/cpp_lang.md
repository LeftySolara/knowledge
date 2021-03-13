# C++

## General Tips

- Difference between `constexpr` and `const`
  - `const` prevents variables from being modified, `constexpr` tells the compiler that an expression results in a compile-time constant
  - Only values known at compile time can be assigned to `constexpr`
  - When applied to functions, `const` can only be used for non-static member functions
    - Guarentees the member function does not modify any non-static data members
  - `constexpr` can be used with member and non-member functions
    - Declares function fit for use in constant expressions
    - Arguments and return types must be literal types

## Links

- [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)
- [Programming: Principles and Practice Using C++ (2nd Edition)](https://www.amazon.com/gp/product/0321992784/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1) (book)
- [Stackoverflow - Difference Between 'constexpr' and 'const'](https://stackoverflow.com/questions/14116003/difference-between-constexpr-and-const)
