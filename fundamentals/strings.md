# Strings

In C++, there are two types of strings: objects of the the String class, and C-strings (also called C-style Strings).

### C-strings

C-strings are arrays of type `char` terminated with the null character, `\0`.

There are multiple ways of declaring a C-string:

```cpp

char str[] = "word";

char str[5] = "word";

char str[] = {'w', 'o', 'r', 'd', '\0'};

char str[5] = {'w', 'o', 'r', 'd', '\0'};

```

The extraction operator `>>` works as `scanf()` in C and considers a space `' '` as the terminating character.

```cpp

#include <iostream>

int main() {
  char str[100];
  std::cin >> str;
  std::cout << strl << std::endl;

  return 0;
}

```

Reading an entire line of text can be done using the `cin.getline()` function, which is a method of the `istream` object and takes in two arguments. The first argument is the address of the first element of the C-string and the second argument is the maximum size of the array.

```cpp

#include <iostream>

int main() {
  char str[100];
  std::cin.getline(str, 100);
  std::cout << str << std::endl;

  return 0;
}

```

### Useful Character Functions

The `<cctype>` header file declares a set of functions to classify (and transform) individual characters. Each function takes in a numerical value representing the ASCII code of one character.

| Function Name | Description                            |
| ------------- | -------------------------------------- |
| `isalnum`     | Checks if a character is alphanumeric. |
| `isalpha`     | Checks if a character is alphabetic.   |
| `isdigit`     | Checks if a character is a digit.      |
| `islower`     | Checks if a character is lowercase.    |
| `isupper`     | Checks if a character is uppercase.    |
| `tolower`     | Converts a character to lowercase.     |
| `toupper`     | Converts a character to uppercase.     |

### Useful Functions For Working With C-strings

The `<cstring>` header file contains some functions for working with C-style strings.

1. `strcpy()` copies a C-string from source to destination.

_Prototype_:

```cpp

char* strcpy(char* dest, const char* src);

```

_Example_:

```cpp

#include <iostream>
#include <cstring>

int main() {
  char src[] = "Hello World!";
  char dest[20];

  strcpy(dest, src);
  std::cout << dest;

  return 0;
}

```

2. `strcat()` appends a copy of a C-string to the end of another C-string.

_Prototype_:

```cpp

char* strcat(char* dest, const char* src);

```

_Example_:

```cpp

#include <iostream>
#include <cstring>

int main() {
  char src[10] = "World!";
  char dest[50] = "Hello ";

  strcat(dest, src);
  std::cout << dest;

  return 0;
}

```

3. `strcmp()` compares two C-strings.

_Prototype_:

```cpp

strcmp(const char* lhs, const char* rhs);

```

`lhs` stands for "left hand side", and `rhs` stands for "right hand side".

_Example_:

```cpp

#include <iostream>
#include <cstring>

int main() {
  char str1[] = "Megadeth";
  char str2[] = "Metallica";

  int result = strcmp(str1, str2);
  std::cout << result;

  return 0;
}

```

_It returns_:

- a positive value if the first differing character in `lhs` is greater than the corresponding character in `rhs`.
- a negative value if the first differing character in `lhs` is less than the corresponding character in `rhs`.
- `0` if `lhs` and `rhs` are equal.

4. `strchr()` searches for the first occurrence of a character in a C-string.

_Prototype_:

```cpp

const char* strchr(const char* str, int ch);
char* strchr(char* str, int ch);

```

_Example_:

```cpp

#include <iostream>
#include <cstring>

int main() {
  char str[] = "Programming is easy.";
  char ch = 'r';

  if (strchr(str, ch))
    std::cout << ch << " is present in \"" << str << "\"";
  else
    std::cout << ch << " is not present in \"" << str << "\"";

  return 0;
}

```

_Return value_:

If the character is found, the `strchr()` function returns a pointer to the location of the character in `str`, otherwise returns the `NULL` pointer.

5. `strstr()` finds the first occurrence of a substring in a c-string.

_Prototype_:

```cpp

const char* strstr(const char* str, const char* target);
char* strstr(char* str, const char* target);

```

_Example_:

```cpp

#include <iostream>
#include <cstring>

int main() {
  char str[] = "Programming is easy.";
  char target[] = "easy";
  char *p = strstr(str, target);

  if (p)
    std::cout << "'" << target << "' is present in \"" << str << "\" at position " << p - str;
  else
    std::cout << target << " is not present \"" << str << "\"";

  return 0;
}

```

_Return value_:

If the substring is found, the `strstr()` function returns a pointer to the first character of the substring, otherwise returns the `NULL` pointer.

If `target` is empty, then the function returns a pointer to the first character of `str`.

6. `strtok()` returns the next token in a C-string.

"Tokens" are smaller chunks of a string that are separated by a specified character, called the delimiting character.

_Prototype_:

```cpp

strtok(char* str, const char* delim);

```

_Example_:

```cpp

#include <iostream>
#include <cstring>

int main() {
  char quote[] = "Remember me when you look at the moon!";
  char* word = strtok(quote, " ");

  std::cout<< word;

  return 0;
}

```

_Return value_:

The `strtok()` function returns a pointer to the next token if there is any, and `NULL` if no more tokens are found.

_Multiple calls_:

It can be called multiple times to obtain tokens from the same string. When the `str` parameter is `NULL`, the call is considered as a subsequent call and the function continues from where it left off.

```cpp

#include <iostream>
#include <cstring>

int main() {
  char str[] = "Remember me when you look at the moon!";
  char delim[] = " ";

  char *token = strtok(str,delim);
  while (token) {
    std::cout << token << std::endl;
    token = strtok(NULL, delim);
  }

  return 0;
}

```

7. `strlen()` returns the length of a C-string.

_Prototype_:

```cpp

strlen(const char* str);

```

_Example_:

```cpp

#include <iostream>
#include <cstring>

int main() {
  char str[] = "Remember me when you look at the moon!";
  std::cout << strlen(str);

  return 0;
}

```

### Adding and Deleting Characters in C-strings

Adding and deleting characters in C-strings can easily be done with pointer arithmetic.

```cpp

#include <iostream>
#include <cstring>

int main() {
  char str[] = "Hey!";
  strcpy(str + 1, str + 2);
  std::cout << str << std::endl;

  strcpy(str + 2, str + 1);
  str[1] = 'e';
  std::cout << str << std::endl;

  return 0;
}

```

### String Objects

String objects are instances of the `string` class from the `<string>` library. Unlike C-strings, they're size is dynamic.

```cpp

#include <iostream>
#include <string>

int main() {
  std::string str = "Hello ";
  str += "World!";
  std::cout << str;

  return 0;
}

```

To read an entire line of text into a string, use the `getline()` function from the `<string>` library which takes an input stream as the first parameter, and a string object as the second.

```cpp

#include <iostream>
#include <string>

int main() {
  std::string str;
  getline(std::cin, str);
  std::cout << str;

  return 0;
}

```

### Useful Functions For Working With Strings

A comprehensive list of methods belonging to a string object can be found [here](https://www.cplusplus.com/reference/string/string/).
