# C++ Programming Exercises

This README file provides a collection of C++ programming exercises along with their implementations. Each program addresses a specific problem or task.

## Table of Contents
1. [Q1. Write a program that reads in two integers and determines and prints if the first is a multiple  of the second. 
](#1-multiple-check)
2. [Q2. Write a program that reads in the size of the side of a square and then prints a hollow square of that size out of asterisks and blanks.Your program should work for squares of all side sizes between 1 and 20.For example, if your program reads a size of 5, it should print ](#2-hollow-square)
```
                *****
                *   *
                *   *
                *   *
                *****                 
```
   
4. [Write a program that reads in a five-digit integer and determines whether it is a palindrome](#3-palindrome-check)
5. [Write a program that computes the value of e^x  by using the formula e^x = 1+x/1! + x/2! + (x^2)/2! + (x^3)/3! + ......](#4-exponent-calculation)
6. [Write a function gcd that returns the greatest common divisor of two integers.](#5-rounding-numbers)
7. [Write a program to solve the Towers of Hanoi problem. Use a recursive function with four parameters:](#6-greatest-common-divisor)
8. [Towers of Hanoi](#7-towers-of-hanoi)
9. [Write a program that inputs a line of text, tokenizes the line with function strtok and outputs the tokens in reverse order. (e.g. for input “Hello dear students” output will be “students” “dear” “Hello”)](#8-tokenize-and-reverse)
10. [Complex Numbers](#9-complex-numbers)
11. [String Concatenation](#10-string-concatenation)
12. [Complex Number Enhancements](#11-complex-number-enhancements)
13. [Shape Hierarchy](#12-shape-hierarchy)
14. [Function Template](#13-function-template)
15. [Exception Handling](#14-exception-handling)
16. [Destructor Call Order](#15-destructor-call-order)
17. [Constructor Failure](#16-constructor-failure)

### 1. Multiple Check
```cpp

#include <iostream>

class SquarePrinter {
public:
    void printHollowSquare(int size) {
        for (int i = 1; i <= size; ++i) {
            for (int j = 1; j <= size; ++j) {
                if (i == 1 || i == size || j == 1 || j == size) {
                    std::cout << "* ";
                } else {
                    std::cout << "  ";
                }
            }
            std::cout << std::endl;
        }
    }
};

int main() {
    int size;

    std::cout << "Enter the size of the square (1 to 20): ";
    std::cin >> size;

    if (size >= 1 && size <= 20) {
        SquarePrinter printer;
        printer.printHollowSquare(size);
    } else {
        std::cout << "Invalid size. Please enter a size between 1 and 20." << std::endl;
    }

    return 0;
}




```


## 2. Hollow Square

**[Move Up](#table-of-contents)**


```cpp

#include <iostream>

class SquarePrinter {
public:
    void printHollowSquare(int size) {
        for (int i = 1; i <= size; ++i) {
            for (int j = 1; j <= size; ++j) {
                if (i == 1 || i == size || j == 1 || j == size) {
                    std::cout << "* ";
                } else {
                    std::cout << "  ";
                }
            }
            std::cout << std::endl;
        }
    }
};

int main() {
    int size;

    std::cout << "Enter the size of the square (1 to 20): ";
    std::cin >> size;

    if (size >= 1 && size <= 20) {
        SquarePrinter printer;
        printer.printHollowSquare(size);
    } else {
        std::cout << "Invalid size. Please enter a size between 1 and 20." << std::endl;
    }

    return 0;
}




```


## 3. Palindrome Check

**[Move Up](#table-of-contents)**

```cpp
#include <iostream>

class PalindromeChecker {
public:
    bool isPalindrome(int num) {
        int originalNum = num;
        int reversedNum = 0;

        while (num > 0) {
            int digit = num % 10;
            reversedNum = reversedNum * 10 + digit;
            num /= 10;
        }

        return originalNum == reversedNum;
    }
};

int main() {
    int fiveDigitNum;

    std::cout << "Enter a five-digit integer: ";
    std::cin >> fiveDigitNum;

    if (fiveDigitNum >= 10000 && fiveDigitNum <= 99999) {
        PalindromeChecker checker;
        if (checker.isPalindrome(fiveDigitNum)) {
            std::cout << fiveDigitNum << " is a palindrome." << std::endl;
        } else {
            std::cout << fiveDigitNum << " is not a palindrome." << std::endl;
        }
    } else {
        std::cout << "Invalid input. Please enter a five-digit integer." << std::endl;
    }

    return 0;
}







```






## 4. Exponent Calculation

**[Move Up](#table-of-contents)**

```cpp

#include <iostream>
#include <cmath>
class ExponentialCalculator {
public:
ExponentialCalculator(double x) : x_(x) {}
double factorial(int n) {
if (n == 0 || n == 1) {
return 1;
} else {
return n * factorial(n - 1);
}

}
double calculateExponential() {
double result = 1.0;
for (int i = 1; i <= 10; ++i) {
result += std::pow(x_, i) / factorial(i);
}
return result;
}
private:
double x_;
};
int main() {
double x;
std::cout << "Enter the value of x: ";
std::cin >> x;
ExponentialCalculator calculator(x);
double result = calculator.calculateExponential();
std::cout << "e^" << x << " is approximately: " << result << std::endl;
return 0;
}


```


## 5. Rounding numbers
**Write a program that defines four functions to round a number x in various ways:
    a.  roundToInteger( number )
    b.  roundToTenths( number )
    c.  roundToHundredths( number )
    d.  roundToThousandths( number )
For each value read, your program should print the original value, the number rounded to the nearest integer, the number rounded to the nearest tenth, the number rounded to the nearest hundredth and the number rounded to the nearest thousandth.**



**[Move Up](#table-of-contents)**

```cpp

 #include <iostream>
#include <cmath>

class RoundingFunctions {
public:
    int roundToInteger(double number) {
        return static_cast<int>(std::round(number));
    }

    double roundToTenths(double number) {
        return std::round(number * 10) / 10;
    }

    double roundToHundredths(double number) {
        return std::round(number * 100) / 100;
    }

    double roundToThousandths(double number) {
        return std::round(number * 1000) / 1000;
    }
};

int main() {
    RoundingFunctions rounding;

    double input;
    std::cout << "Enter a number: ";
    std::cin >> input;

    std::cout << "Original value: " << input << std::endl;
    std::cout << "Rounded to nearest integer: " << rounding.roundToInteger(input) << std::endl;
    std::cout << "Rounded to nearest tenth: " << rounding.roundToTenths(input) << std::endl;
    std::cout << "Rounded to nearest hundredth: " << rounding.roundToHundredths(input) << std::endl;
    std::cout << "Rounded to nearest thousandth: " << rounding.roundToThousandths(input) << std::endl;

    return 0;
}





```

## 6. Greatest Common Divisor

**[Move Up](#table-of-contents)**

```cpp
#include <iostream>

int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int main() {
    int num1, num2;
    std::cout << "Enter two integers: ";
    std::cin >> num1 >> num2;

    int result = gcd(num1, num2);

    std::cout << "GCD of " << num1 << " and " << num2 << " is: " << result << std::endl;

    return 0;
}




```



## 7. Towers of Hanoi
**Write a program to solve the Towers of Hanoi problem. Use a recursive function with four parameters:
         a.  The number of disks to be moved
         b. The peg on which these disks are initially threaded
         c. The peg to which this stack of disks is to be moved
         d. The peg to be used as a temporary holding area**
         
**[Move Up](#table-of-contents)**

```cpp

#include <iostream>

void towersOfHanoi(int disks, char source, char destination, char auxiliary) {
    if (disks == 1) {
        std::cout << "Move disk 1 from " << source << " to " << destination << std::endl;
        return;
    }

    towersOfHanoi(disks - 1, source, auxiliary, destination);
    std::cout << "Move disk " << disks << " from " << source << " to " << destination << std::endl;
    towersOfHanoi(disks - 1, auxiliary, destination, source);
}

int main() {
    int numDisks;
    std::cout << "Enter the number of disks: ";
    std::cin >> numDisks;

    towersOfHanoi(numDisks, 'A', 'C', 'B');

    return 0;
}


```



## 8. Tokenize and Reverse

**[Move Up](#table-of-contents)**


```cpp

#include <iostream>
#include <cstring>
#include <stack>

int main() {
    const int MAX_LENGTH = 1000;
    char input[MAX_LENGTH];

    std::cout << "Enter a line of text: ";
    std::cin.getline(input, MAX_LENGTH);

    // Tokenize using strtok
    char *token = strtok(input, " ");
    std::stack<std::string> tokens;

    while (token != nullptr) {
        tokens.push(token);
        token = strtok(nullptr, " ");
    }

    // Output tokens in reverse order
    std::cout << "Tokens in reverse order: ";
    while (!tokens.empty()) {
        std::cout << tokens.top() << " ";
        tokens.pop();
    }

    std::cout << std::endl;

    return 0;
}




```


## 9. Complex Numbers
**Create a class called Complex for performing arithmetic with complex numbers. Write a driver program to test your class. Complex numbers have the form realPart + 
  imaginaryPart * i         
     Provide public member functions for each of the following:
        a) Addition of two Complex numbers: The real parts are added together and the imaginary parts are added together.
        b) Subtraction of two Complex numbers: The real part of the right operand is subtracted from the real part of the left operand and the imaginary part of the 
           right operand is subtracted from the imaginary part of the left operand.
        c) Printing Complex numbers in the form (a, b) where a is the real part and b is the imaginary part.**


**[Move Up](#table-of-contents)**

```cpp

#include <iostream>

class Complex {
private:
    double realPart;
    double imaginaryPart;

public:
    Complex(double real, double imaginary) : realPart(real), imaginaryPart(imaginary) {}

    Complex add(const Complex& other) const {
        return Complex(realPart + other.realPart, imaginaryPart + other.imaginaryPart);
    }

    Complex subtract(const Complex& other) const {
        return Complex(realPart - other.realPart, imaginaryPart - other.imaginaryPart);
    }

    void print() const {
        std::cout << "(" << realPart << ", " << imaginaryPart << ")";
    }
};

int main() {
    Complex complex1(2.5, 3.0);
    Complex complex2(1.5, 2.0);

    Complex sum = complex1.add(complex2);
    Complex difference = complex1.subtract(complex2);

    std::cout << "Complex 1: ";
    complex1.print();
    std::cout << std::endl;

    std::cout << "Complex 2: ";
    complex2.print();
    std::cout << std::endl;

    std::cout << "Sum: ";
    sum.print();
    std::cout << std::endl;

    std::cout << "Difference: ";
    difference.print();
    std::cout << std::endl;

    return 0;
}



```



## 10. String Concatenation

**[Move Up](#table-of-contents)**


```cpp



```


## 11. Complex Number Enhancements

**[Move Up](#table-of-contents)**


```cpp



```


## 12. Shape Hierarchy

**[Move Up](#table-of-contents)**


```cpp



```


## 13. Function Template

**[Move Up](#table-of-contents)**


```cpp



```


## 14. Exception Handling

**[Move Up](#table-of-contents)**

```cpp



```



## 15. Destructor Call Order

**[Move Up](#table-of-contents)**

```cpp



```




## 16. Constructor Failure

**[Move Up](#table-of-contents)**


   
```cpp



```

 




