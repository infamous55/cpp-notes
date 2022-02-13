# Introduction

C++ was developed by Bjarne Stroustrup in 1979, and it adds object-oriented programming and many other features to the C language. It is fast, flexibile, and well-suported across numerous platforms, with applications in systems programming, embedded software, desktop applications, video games, and servers.

### Program Structure

The specific file extension is `.cpp`. The program runs line by line, from top to bottom. `#include` statements are written at the beginning of any program, while the `main()` function is the only one that runs by default. `return 0` at the end indicates that the program ran without issues.

```cpp

#include <iostream>

int main() {
  std::cout << "Hello World!\n";
  return 0;
}

```

### Compilation

C++ is a compiled language. Run `g++` and the filename to compile the program, then execute it with `./` followed by the name of the executable.

```sh

g++ hello.cpp -o hello && ./hello

```
