# C++ Cheat Sheets List:

### home

| Title                           | Remark         |
| ------------------------------- | -------------- |
| [Introduction](#introduction)   | 開発環境設置等 |
| [Number](#number)               |                |
| [Random Number](#random-number) |                |

[Home](#home)

### Introduction

- C++ was updated 4 major times in 2011, 2014, 2017, and 2020 to C++11, C++14, C++17, C++20.

| Statically-typed | Dynamically-typed |
| ---------------- | ----------------- |
| C++              | Python            |
| C#               | JavaScript        |
| Java             | Ruby              |

- 開発環境設置
  <img src="./aasets/setup.png" />

```c++
#include <iostream>

using namespace std; // using directive to pick up the std namespace to eliminate std:: in the code for example std::cout
int main(){

   int input_number = 0;
   cin >> input_number; // reading data from the console
   cout << input_number; // output data to the console

   return 0;
}
```

[Home](#home)

### Number

- Type of Number

| Type        | Bytes | Range                |
| ----------- | ----- | -------------------- |
| short       | 4     | -32,768 to 32,767    |
| int         | 4     | -2B to 2B            |
| long        | 4     | -2B to 2B            |
| long long   | 8     |                      |
| float       | 4     | -3.4E38 to 3.4E38    |
| double      | 8     | -1.7E308 to 1.7E308  |
| long double | 8     | -3.4E932 to 1.7E4832 |
| bool        | 1     | true/false           |
| char        | 1     |                      |

```c++
// the F is important, if without F by default the compiler will treat htis number as a double
// and then it will try to store a double inside a float variable and this can potentially
// cause data loss
float interestRate = 3.67F;

// Without L the compiler will treat this number as integer
long fileSize = 900000L;

// auto keyword it kind of makes our code shorter and more consistent
// auto keyword is very useful when working with more complex types
auto isValid = false;

auto interestRate = 3.67F; // this will give you float number
auto interestRate = 3.67; // this will give you integer

```

- brace initializer
  - modern way to initialize variable in c++

```c++
// by using brace initialization the compiler can detect
// the error and give you the red underline
int number{1.2};

// if you supply nothing the number variable will be initialized to zero
int number{};
cout << number; // will output 0
```

[Home](#home)

| System               | Digits  | Example  |
| -------------------- | ------- | -------- |
| Decimal(Base 10)     | 0-9     | 255      |
| Binary(Base 2)       | 0,1     | 11111111 |
| Hexadecimal(Base 16) | 0-9 A-F | FF       |

- Hexadecimal used to shorten binary number, are more compact, in programming we use it to represent colors
- using only six digits of a hexadecimal number we can represent any color
  RGB = Red(FF) Green(00) Blue(00) = FF 00 00

```c++
 int number = 0b11111111; // use 0b to print binary number
 int number = 0xFF; // use 0x to print Hexadecimal number
 cout << number; // output 255
```

- narrowing
  - initialize a variable of a smaller type using a larger type

```c++
int number = 1'000'000; // c++ let you make the number look better by letting you use the single quote to separate the digit
short another = number; // converting an integer to a short is a narrowing
cout << another; // output 1690 this is the result of narrowing convertion which is data loss
```

- you can use brace initializer to prevent the narrowing error `short another{number};`

[Home](#home)

### Random Number

```c++
#include <cstdlib>
#include <ctime> // library to use time() which return the current time in terms of number of seconds
                 // elapsed from January 1st 1970

using namespace std;
int main(){
   int number = rand(); // this will only generate the random number for one-time.

   time(0); // to call this function have to give it a special argumnet called null pointer or null ptr
   long elapsedSeconds = time(0); // Jan 1 1970
   srand(elapsedSeconds); // this is the formula for the rand();
   int number = rand();
   cout << number; // now everytime you reload you will get random number

}
```

- tutorial: rolling dice with the formula `[ rand() % ( maxValue - minValue + 1 )] + minValue`

```c++
#include <cstdlib>
#include <ctime>

using namespace std;
int main(){

   const short minValue = 1;
   cons short maxValue = 6;

   srand(time(0));
   short first = (rand()%(maxValue-minValue+1)) + minValue;
   short second = (rand()%(maxValue-minValue+1)) + minValue;

   cout << first << ", " << second;

   return 0;
}
```
