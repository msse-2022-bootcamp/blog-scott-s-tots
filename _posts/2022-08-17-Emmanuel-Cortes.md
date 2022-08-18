---
layout: post
title: "C++: Functions, Namespaces and Exceptions"
author: Emmanuel Cortes
---

## Quick Python Function Review
As we learned last week, Python function signature at minimum consists of `def` keyword, function name, argument list and a semicolon at the end. Python functions argument types are dynamic as well are it's return type(s).
```Python
def func(arg1, arg2):
    pass
```

Python differs greatly from C++ in regards to the number of return values. Python functions automatically return a tuple with all return values. The calling code can then unpack the returning tuple.
```Python
def swap(arg1, arg2):
    return arg2, arg1

a, b = swap(1, 2)  # (2,  1)  tuple
print(a)  # 2
print(b)  # 1
```

## C++ Functions
In C++, however, the function signature requires a return type, function name, argument list, and braces to enclose the definition (whitespace is insignificant). 

### void 
The argument list must also provide their type. If the function doesn't return a value or no value is passed to the function then you must specify as such, with the keyword `void`.
```C++
int func(int arg1, double arg2)
{
    return 0;
}

void devoid(void)
{
}
```

### Function argument
C++ provides diverse method of passing variables/objects.
You can:
- pass by value
- pass by pointer
- pass by reference

#### Pass by value
Pass by value entails passing a copy of the variable as an argument. The function then utilizes and modifies the new variable. The new variable is scoped to the function (within the `{}`). 

This is useful for making the variable immutable thus protecting the variables from modification.

#### Pass by pointer
Pass by pointer instead requires you to specify that the argument type is a pointer (`int*`). In the function you can then dereference the pointer with `*` (i.e. `*pointer`). Thus you are able to modify the passed variables.


In general, you should avoid pointers unless required. Even then you can use [smart pointers](https://stackoverflow.com/a/569931).
```C++
int v = 1;
int*  i = v;
int* func(int* arg)
{
    *arg = 2;  // changes the value stored at the memory location the pointer points to
}
```

#### Pass by reference
Pass by reference allows you take advantage of pointers without the hassle of referencing and dereferencing. Instead of passing a copy of the variable, with pass by reference, an alias is created for the original variable. Allow you to:
1. Modify the original variable
1. Prevent the creation of a new variable
    - an issue when working with large abstract data types

### Const 
To prevent the modification of a variable of a reference, then add the `const` keyword to declaration statements and function calls
```
const PI = 3.14159
int& func(const int& arg)
{
    arg = 3;  // changes th
}
```


## Namespaces
Namespaces scope code under a common identifier and are similar to python modules.
Namespace have two main purposes:
- Group functions
    - Similar to our Python mc-package
- Prevent collision
    - Different libraries might define a function with the same name
    - Python has something similar where if you append 

To access variables or functions in a namespace, you must provide the namespace and scope resolution operator `::`.
```C++
namespace ns 
{
    int i = 1;  // accessed as ns::i
    void func(void)  // accessed as ns::func()
    {
    }
}
```


## Errors and Error Handling
To handle an error you need to wrap the offending code a `try-catch` statement. While in the catch block, you can access the error text using the `std::exception.what()` member function. Don't forget to return an non-zero integer to denote failure. [Link on modern C++ exception and error handling](https://docs.microsoft.com/en-us/cpp/cpp/errors-and-exception-handling-modern-cpp?view=msvc-170).
```C++
try {
    // code
}
catch(std::exception& ex)
{
    std::cout << "Exception: " << ex.what() << std::endl;
    return 1
}
```


In Python you `raise` an exception and C++ you `throw` an exception. Additionally, in Python you should specify the type of error (ValueError, IndexError).
```Python
try:
    # code
    a = 1 / 0
    if x == 0:
       raise IndexError;
except (ZeroDivisionError, IndexError):
    # error handling code
    pass
```
