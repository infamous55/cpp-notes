# Functions

Functions are reusable blocks of code. They are either predefined in the Standard Library or user-defined.

### Declaration and Definition

A C++ function has two parts: the declaration and the definition.

The declaration includes the return type, the function name, and the parameters. It is also called prototype or signature. Function declarations are generally stored in a header file (`.hpp` or `.h`).

The definition is the body of the function which containes the code that executes at call. It is common to store function definitions in a separate `.cpp` file. If the file containing the `main()` function needs to be recompiled, it is not necessary to recompile the other files.

A function can be called by specifying its name followed by a pair of parentheses `()`.

```cpp

#include <iostream>

void print(int);

int main() {
  print(10);
  return 0;
}

void print(int x) {
  std::cout << x;
}

```

### Parameters and Arguments

Parameters are placeholders for values passed to the function. They act as variables inside the function.

The values passed are known as arguments. They represent the actual input values. Default arguments can be added to function declarations so that it is possible to call the function without including those arguments. If those arguments are included the default value is overwritten.

```cpp

void display(char c = '*', int count = 3) {
  for (int i = 1; i <= count; ++i) {
    std::cout << c;
  }
  std::cout << std::endl;
}

```

### Return

The `return` statement can be used to return a value from a function. It terminates the function, so any code after `return` won't run.

The data type of the returned value must match the declared function type. When there is no value returned, the `void` type is used.

### Scope

The scope is the region of code that can access or view a given element:

Variables defined in global scope are accessible throughout the program.

Variables defined in a function have local scope and are only accessible inside the function.

### Overloading

In C++, two functions can have the same name if the number and/or type of arguments passed is different. These functions are known as overloaded functions.

The function return type is not used to differentiate overloaded functions.

```cpp

#include <iostream>

int add(int a, int b) {
  return a + b;
}

double add(double a, double b) {
  return a + b;
}

int add(int a, int b, int c = 0) {
  return a + b + c;
}

int main() {
  std::cout << add(3, 2) << std::endl;
  std::cout << add(5.3, 1.4) << std::endl;
  std::cout << add(2, 6, 9) << std::endl;

  return 0;
}

```

### Pass by Reference and Return by Reference

The `&` operator is used to indicate that a parameter is passed by reference, so that the function can modify it.

```cpp

void swap(int& x, int& y) {
  int aux;
  aux = x;
  x = y;
  y = aux;
}

```

It is also possible to return values by reference.

```cpp

#include <iostream>

int num;

int& test();

int main() {
  test() = 5;
  std::cout << num;

  return 0;
}

int& test() {
  return num;
}

```

### Command Line Arguments

Command line arguments are optional arguments passed to the `main()` function of a C++ program.

In order to access command line arguments, the new form of `main()` takes two arguments:

- `argc`: the number of command line arguments,
- `argv`: an array containing the values of command line arguments.

```cpp

#include <iostream>

int main(int argc, char* argv[]) {
  std::cout << argc << std::endl;

  for (int i = 0; i < argc; i++) {
    std::cout << argv[i] << std::endl;
  }

  return 0;
}

```
