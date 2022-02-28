# Basics

### Variables and Constants

When declaring a variable, it must be given a data type and a name. The name can only have letters, numbers, and underscores, it cannot begin with a number, and cannot be a reserved keyword.

Multiple variables of the same type can be declared in a single statement using a comma-separated list.

Constants can be declared with the const keyword, which prevents their value from being changed later.

```cpp

int age = 18;

char letter;
letter = 'c';

const float pi = 3.14;

```

### Fundamental Data Types

The table below shows the fundamental data types, their meaning, and their sizes:

| Data Type | Meaning               | Size (in bytes) |
| --------- | --------------------- | --------------- |
| `int`     | Integer               | 2 or 4          |
| `float`   | Floating-point        | 4               |
| `double`  | Double Floating-point | 8               |
| `char`    | Character             | 1               |
| `wchar_t` | Wide Character        | 2               |
| `bool`    | Boolean               | 1               |
| `void`    | Empty                 | 0               |

\*Note: Variables cannot be declared of type `void`.

### Type Modifiers

The data types `int`, `double`, and `char` can be modified by using type modifiers. There are 4 type modifiers in C++. They are:

- `signed`
- `unsigned`
- `short`
- `long`

### Modified Data Types

The table below shows the modified data types, their sizes, and their meaning:

| Data Type            | Size (in bytes) | Meaning                                                                             |
| -------------------- | --------------- | ----------------------------------------------------------------------------------- |
| `signed int`         | 4               | used for integers (equivalent to `int`)                                             |
| `unsigned int`       | 4               | can only store positive integers                                                    |
| `short`              | 2               | used for small integers (range -32768 to 32767)                                     |
| `unsigned short`     | 2               | used for small positive integers (range 0 to 65,535)                                |
| `long`               | at least 4      | used for large integers (equivalent to `long int`)                                  |
| `unsigned long`      | 4               | used for large positive integers or 0 (equivalent to `unsigned long int`)           |
| `long long`          | 8               | used for very large integers (equivalent to `long long int`).                       |
| `unsigned long long` | 8               | used for very large positive integers or 0 (equivalent to `unsigned long long int`) |
| `long double`        | 12              | used for large floating-point numbers                                               |
| `signed char`        | 1               | used for characters (guaranteed range -127 to 127)                                  |
| `unsigned char`      | 1               | used for characters (range 0 to 255)                                                |

### Input and Output

To access input and output, the `iostream` header file must be included at the beginning of the program. The `std::cout` object is used together with `<<` operator to print to the terminal, and `std::cin` is used together with `>>` to read user input. The `std::endl` object or the `\n` character can be used to insert a new line.

```cpp

#include <iostream>
#include <string>

int main() {
  std::string name;
  int age;
  std::cout << "Please enter your name and age: ";
  std::cin >> name >> age;
  std::cout << "Your name is " << name << " and you are " << age << " years old.";

  return 0;
}

```

### Type Conversion

Converting from one data type from another is called type conversion. In C++, type conversion is of two types: _implicit_ and _explicit_.

**Implicit type conversion** is done automatically by the compiler.

```cpp

#include <iostream>

int main() {
  int num_int = 9;
  double num_double;

  num_double = num_int;

  std::cout << "num_int = " << num_int << std::endl;
  std::cout << "num_double = " << num_double << std::endl;

  return 0;
}

```

**Explicit type conversion** is when the user manually changes data from one type to another. This is also known as _type casting_.

The syntax for C-style type casting is `(data_type)expression;`.

The syntax for function-style casting is `data_type(expression);`.

```cpp

#include <iostream>

int main() {
  double num_double = 3.56;
  std::cout << "num_double = " << num_double << std::endl;

  int num_int1 = (int)num_double;
  std::cout << "num_int1 = " << num_int1 << std::endl;

  int num_int2 = int(num_double);
  std::cout << "num_int2 = " << num_int2 << std::endl;

  return 0;
}

```

### Arithmetic Operators

C++ supports different types of arithmetic operators that can perform common mathematical operations:

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division
- `%` modulo

### Increment and Decrement Operators

C++ also provides increment and decrement operators: `++` and `--` respectively.

- `++` increases the value of the operand by 1
- `--` decreases it by 1

Using the increment or the decrement operator as a prefix modifies the variable, and then returns the value.

Using the increment or the decrement operator as a postfix returns the original value, then modifies the variable.

### Assignment Operators

In C++, assignment operators are used to assign values to variables.

| Operator | Example   | Equivalent to |
| -------- | --------- | ------------- |
| `=`      | `a = b;`  | `a = b;`      |
| `+=`     | `a += b;` | `a = a + b;`  |
| `-=`     | `a -= b;` | `a = a - b;`  |
| `*=`     | `a *= b;` | `a = a * b;`  |
| `/=`     | `a /= b;` | `a = a / b;`  |
| `%=`     | `a %= b;` | `a = a % b;`  |

### Relational Operators

A relational operator is used to check the relationship between two operands.

| Operator | Meaning                  |
| -------- | ------------------------ |
| `==`     | Is Equal To              |
| `!=`     | Not Equal To             |
| `>`      | Greater Than             |
| `<`      | Less Than                |
| `>=`     | Greater Than or Equal To |
| `<=`     | Less Than or Equal To    |

### Logical Operators

Logical operators are used to check whether an expression is `true` or `false`. If the expression is `true`, it returns `1` whereas if the expression is `false`, it returns `0`.

<!-- prettier-ignore-start -->
| Operator | Meaning     |
| -------- | ----------- |
| `&&`     | Logical AND |
| `\|\|`   | Logical OR  |
| `!`      | Logical NOT |
<!-- prettier-ignore-end -->

### Comments

Single-line comments begin with `//`, and multi-line comments start with `/*` and end with `*\`.

```cpp

// This is a single-line comment.

/*
This is a
multi-line
comment.
*/

```
