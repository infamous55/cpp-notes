# Miscellaneous

### Namespaces

A namespace is a declarative region that provides a scope to the identifiers inside of it.

The syntax for declaring a namespace is as follows:

```cpp

namespace my_namespace {
  int age = 18;
}

```

To access an element from inside a namespace use the scope operator `::`.

```cpp

std::cout << my_namespace::age << std::endl;

```

The `using` keyword allows the use of an identifier from a namespace without preceding it with the respective prefix.

```cpp

using std::cout;

```

The standard namespace is denoted by `std`, and `using namespace std;` is considered bad practice because it can create name collisions.

### Exception Handling

Exception handling in C++ consists of three keywords: `try`, `throw` and `catch`:

The `try` statement allows the definition of a block of code that will be tested for errors while it is being executed.

The `throw` keyword throws an exception when a problem is detected, which lets us create a custom error.

The `catch` statement allows the definition of a block of code that will be executed if an error occurs in the try block.

```cpp

try {
  throw 10;
}
catch (char e) {
  std::cout << "Caught " << e;
}
catch (...) {
  std::cout << "Default Exception\n";
}

```

The `catch (...)` statement can be used to handle all types of exceptions, while normal `catch` statements are type restricted. Implicit type conversion doesn’t happen for primitive types.

A derived class exception should be caught before a base class exception.

```cpp

#include <iostream>

class Base {};
class Derived: public Base {};

int main() {
  Derived d;

  try {
    throw d;
  }
  catch(Base b) {
    std::cout << "Caught Base Exception";
  }
  catch(Derived d) {
    // This catch block is NEVER executed
    std::cout << "Caught Derived Exception";
  }

  return 0;
}

```

C++ library has a standard exception class which is base class for all standard exceptions. All objects thrown by components of the standard library are derived from this class.

All exceptions are unchecked, so the compiler doesn’t check whether an exception is caught or not.

When an exception is thrown, all objects created inside the enclosing `try` block are destructed before the control is transferred to the `catch` block.

### Working With Files

There are three classes included in the `<fstream>` library, which are used to create, write or read files:

| Class       | Description                 |
| ----------- | --------------------------- |
| `ofstream`  | Creates and writes to files |
| `ifstream ` | Reads from files            |
| `fstream`   | A combination of the above  |

**Creating and writing to a file**

```cpp

#include <iostream>
#include <fstream>

using namespace std;

int main() {
  ofstream fout("filename.txt");
  fout << "Hello World!";
  fout.close();

  return 0;
}

```

**Reading from a file**

```cpp

#include <iostream>
#include <string>
#include <fstream>

using namespace std;

int main() {
  string line;
  ifstream fin("filename.txt");
  while (getline(fin, line)) {
    cout << line << endl;
  }
  fin.close();

  return 0;
}

```
