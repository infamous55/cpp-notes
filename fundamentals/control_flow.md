# Control Flow

### Conditional Statements

Conditional statements are used to control the flow of code execution by testing a condition.

`if` statements execute the following block of code only if the condition is `true`. `else` statements execute code only if the provided condition is `false`. Multiple `else if` statements can be added between `if` and `else` to check for additional conditions.

```cpp

int temperature = 60;

if (temperature < 65) {
  std::cout << "Too cold!";
}
else if (temperature > 75) {
  std::cout << "Too hot!";
}
else
  std::cout << "Just right...";

```

Curly brackets can be ommited if there is only one line of code in the conditional statement.

An `if` - `else` expression can be condensed into a single line statement with the following syntax:

```cpp

variable = (condition) ? condition_is_true : condition_is_false;

```

### Loops

`while` loops repeat a block of code as long as the condition is true, and `do while` loops are similar, but run at least once.

`for` loops repeat code a certain number of steps, and `for-each` loops are used to iterate through every item in a list-like structure.

```cpp

int count = 0;
while (count <= 10) {
  std::cout << count;
  count++;
}

int price = 300;
do {
  std::cout << "Too expensive!";
} while (price > 500);

for (int i = 0; i <= 10; i++) {
  std::cout << i;
}

int fibonacci[5] = { 0, 1, 1, 2, 3 };
for (auto number:fibonacci){
  std::cout << number;
}

```

### Break and Continue

In C++, the `break` keyword is used to exit a switch or loop.

The `continue` keyword is used to skip an iteration of a loop.

```cpp

for (int i = 0; i < 10; i++) {
  if (i == 4) {
    break;
  }
  std::cout << i;
}

for (int i = 0; i < 10; i++) {
  if (i == 4) {
    continue;
  }
  std::cout << i;
}

```

### Switch Statements

Switch statements provide a way to check an expression against multiple possible values.

The `break` keyword can be used to terminate a `case`.

The code within the `default` block is executed when no other `case` matches.

```cpp

switch (grade) {
  case 9:
    std::cout << "Freshman\n";
    break;
  case 10:
    std::cout << "Sophomore\n";
    break;
  case 11:
    std::cout << "Junior\n";
    break;
  case 12:
    std::cout << "Senior\n";
    break;
  default:
    std::cout << "Invalid\n";
    break;
}

```
