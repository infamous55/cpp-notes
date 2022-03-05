# Pointers

### Pointer Variables

In C++, a pointer variable is a variable which stores a memory address. It is created using the `*` sign.

The _address-of_ operator `&` is used to obtain the memory address of a variable, and the dereference operator `*` is used to get the value pointed to by a pointer variable.

```cpp

int number = 5;

int* my_pointer = &number;

std::cout << *my_pointer;

```

A `void` pointer has no associated data type with it and can be typecasted into any type.

```cpp

void print(void* pointer, char type) {
  switch (type) {
    case 'i':
      std::cout << *((int*)pointer);
      break;
    case 'c':
      std::cout << *((char*)pointer);
      break;
  }
}

```

If a pointer points to nothing, it is called a null pointer.

### Reference Variables

A reference variable is an alias, or an alternate name to an existing variable.

When `&` is used in an expression, it acts as the _address-of_ operator. However, when it appears in a declaration, it is used to create a reference variable.

```cpp

int number = 5;
int& ref_number = number;

std::cout << number << " = " << ref_number;

```

### Pass-By-Reference

In C++, _pass-by-reference_ allows to modify the value of the function arguments, and avoid making copies of a variable/object for performance reasons.

It can be done by either using pointer arguments, or using reference arguments.

```cpp

#include <iostream>

void square(int*);

int main() {
  int number = 8;
  std::cout << number << std::endl;
  square(&number);
  std::cout << number << std::endl;

  return 0;
}

void square(int* n) {
  *n *= *n;
}

```

```cpp

#include <iostream>

void square(int&);

int main() {
  int number = 8;
  std::cout << number << std::endl;
  square(number);
  std::cout << number << std::endl;

  return 0;
}

void square(int& n) {
  n *= n;
}

```

### Working with Arrays

An array variable points to the memory address of its first element.

Accessing array elements can be done by either using square brackets `[]`, or using the dereference operator `*`.

```cpp

int my_array = {0, 1, 2, 3, 4};

std::cout << my_array[2] << std::endl;
std::cout << *(my_array + 2) << std::endl;

```

Allocating dynamic memory can be done with the `new` keyword. Memory deallocation is done using the `delete` keyword, and must be done in order to avoid memory leaks.

```cpp

int size;
std::cin >> size;
int* my_array = new int[size];

for (int i = 0; i < size; i++) {
  std::cin >> my_array[i];
}

for (int i = 0; i < size; i++) {
  std::cout << *(my_array + i);
}

delete[] my_array;
my_array = NULL;

```

This is how two-dimensional dynamic arrays can be implemented.

```cpp

int rows, columns;
std::cin >> rows >> columns;
int** table = new int*[rows];

for (int i = 0; i < rows; i++) {
  table[i] = new int[columns];
}

for (int i = 0; i < rows; i++) {
  for (int j = 0; j < columns; j++) {
    std::cin >> table[i][j];
  }
}

for (int i = 0; i < rows; i++) {
  delete[] table[i];
}
delete[] table;
table = NULL;

```

### Function Pointers

Function pointers can be used to pass function as arguments.

```cpp

#include <iostream>
#include <vector>
using namespace std;

bool ascending_compare(int a, int b) {
  return a < b;
}

bool descending_compare(int a, int b) {
  return a > b;
}

void custom_sort(vector<int>& numbers_vector, bool(*compare_function_ptr)(int, int)) {
  for (int start_index = 0; start_index < numbers_vector.size(); start_index++) {
    int best_index = start_index;
    for (int current_index = start_index + 1; current_index < numbers_vector.size(); current_index++) {
      if (compare_function_ptr(numbers_vector[current_index], numbers_vector[best_index]))
        best_index = current_index;
    }
    swap(numbers_vector[start_index], numbers_vector[best_index]);
  }
}

void print_numbers(vector<int>& numbers_vector) {
  for (int i = 0; i < numbers_vector.size(); i++)
    cout << numbers_vector[i] << ' ';
}

int main() {
  vector<int> numbers_vector = {4, 2, 1, 3, 6, 5};
  bool (*func_ptr)(int, int) = descending_compare;
  custom_sort(numbers_vector, func_ptr);
  print_numbers(numbers_vector);

  return 0;
}

```

### Smart Pointers

A smart pointer is a wrapper class over a raw pointer. Unlike a normal pointer, it deallocates and frees memory automatically.

There are three types of smart pointers: `unique_ptr`, `shared_ptr`, `weak_ptr`.

**Unique Pointer**

An unique pointer stores one pointer only. A different object can be assigned by removing the current object from the pointer.

```cpp

#include <iostream>
#include <memory>
using namespace std;

class Rectangle {
public:
  int length;
  int breadth;

  Rectangle(int l, int b) {
    length = l;
    breadth = b;
  }

  int area() {
    return length * breadth;
  }
};

int main() {
  unique_ptr<Rectangle> P1(new Rectangle(10, 5));
  cout << P1->area() << endl;

  unique_ptr<Rectangle> P2;
  P2 = move(P1);

  cout << P2->area() << endl;

  return 0;
}

```

**Shared Pointer**

By using a shared pointer more than one pointer can point to one object at a time and it’ll maintain a _Reference Counter_ using the `use_count()` method.

```cpp

#include <iostream>
#include <memory>
using namespace std;

class Rectangle {
public:
  int length;
  int breadth;

  Rectangle(int l, int b) {
    length = l;
    breadth = b;
  }

  int area() {
    return length * breadth;
  }
};

int main() {
  shared_ptr<Rectangle> P1(new Rectangle(10, 5));
  cout << P1->area() << endl;

  shared_ptr<Rectangle> P2;
  P2 = P1;

  cout << P2->area() << endl;
  cout << P1->area() << endl;

  cout << P1.use_count() << endl;

  return 0;
}

```

**Weak Pointer**

Weak pointers work similarly to shared pointers, except that they do not take ownership of an object but act as an observer. They are mainly used to break circular dependency.

```cpp

#include <iostream>
#include <memory>
using namespace std;

struct Person;

struct Team {
  shared_ptr<Person> leader;
  ~Team() { cout << "Team destructed."; }
};

struct Person {
  weak_ptr<Team> team;
  ~Person() { cout << "Person destructed."; }
};

int main(){
  auto Marketing = make_shared<Team>();
  auto John = make_shared<Person>();

  Marketing->leader = John;
  John->team = Marketing;

  return 0;
}

```
