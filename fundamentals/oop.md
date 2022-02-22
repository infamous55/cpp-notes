# Object-Oriented Programming (OOP)

### Classes and Objects

A class is a user-defined data type that encapsulates information and behavior about an object.

There are two types of class members:

- _Attributes_ represent information about an object.
- _Methods_ are functions that can be used with an object.

An object is an instance of a class and can be created by specifying the class name.

```cpp

#include <iostream>

class Dog {
public:
  int age;

  void sound() {
    std::cout << "woof" << std::endl;
  }
};

int main() {
  Dog buddy;

  buddy.age = 5;
  buddy.sound();

  return 0;
}

```

### Access Specifiers

Access specifiers are keywords that determine the scope of class components.

Class members under the `public` access specifier are accessible from anywhere in the program, while `private` class members are only accessible from inside the class.

Members of the base class under the `protected` access modifier are accessible by the derived class, but not outside the class.

```cpp

class Test {
private:
  int a;
  void function1() {}

public:
  int b;
  void function2() {}

protected:
  int c;
  void function3() {}
};

```

### Encapsulation

Encapsulation is a way of organizing data members and function members.

It is achieved by declaring class attributes as private and having access methods (getters) that return the value of member variables, along with mutator functions (setters) that change the value of those member variables.

```cpp

class Encapsulation {
private:
  int num;

public:
  void setNum(int x) {
    num = x;
  }

  int getNum() {
    return num;
  }
};

```

### Constructors and Destructors

A constructor is a special type of member function that is called automatically when an object is created.

In C++, constructors have the same name as the class they belong to.

A constructor with no parameters is known as a default constructor, and a constructor with parameters is known as a parameterized constructor.

Simillarly, a destructor is a member function which is invoked automatically whenever an object is going to be destroyed.

There can only one destructor in a class with classname preceded by `~`, no parameters and no return type.

```cpp

#include <iostream>
#include <cstring>

class String {
private:
  char* s;
  int size;

public:
  String(char* c) {
    size = strlen(c);
    s = new char[size + 1];
    strcpy(s, c);
  }

  ~String() {
    delete[] s;
  }

  void print() {
    std::cout << s;
  }
};

int main() {
  char s[20]; strcpy(s, "Hello World!");
  String message(s); message.print();

  return 0;
}

```

### Inheritence

Inheritance is the ability to create a new class based on an existing class, starting out with the same existing properties and methods.

In an inheritance relationship, there are two categories of classes:

- _Base class_: The class being inherited from.
- _Derived class_: The class that inherits from the base class.

Access modes determine the access modifiers of the inherited members.

It’s also possible to have multi-level inheritance.

```cpp

class Shape {
public:
  int center[2];
  int weight;
  int color;

  void translate(int deltaX, int deltaY) {
    center[0] += deltaX;
    center[1] += deltaY;
  }
};

class Rectangle: public Shape {
public:
  int height;
  int width;

  int perimeter() {
    return (height + width) * 2;
  }
};

class Circle: public Shape {
public:
  int radius;

  float circumference() {
    return 2.0 * 3.1416 * float (radius);
  }
};

```

### Polymorphism

Polymorphism gives a function or method "many forms".

In C++, there are two types of polymorphism: compile-time and runtime.

Compile-time polymorphism can be implemented using function overloading or operator overloading.

```cpp

class Add {
public:
  int sum(int num1, int num2) {
    return num1 + num2;
  }

  int sum(int num1, int num2, int num3) {
    return num1 + num2 + num3;
  }
};

```

Function overriding is an example of runtime polymorphism.

```cpp

class A {
public:
  void print() {
    std::cout << "Output: Parent Class Function" << "\n";
  }
};

class B: public A {
public:
  void print() {
    std::cout << "Output: Child Class Function" << "\n";
  }
};

```
