# Week 1 – Setup, Java Basics, Primitive Data Types & Variables

---

## Why Learn This?

Understanding Java’s syntax and primitive data types is like learning the alphabet before writing words. This foundation enables you to:

* Build reliable, efficient programs.
* Understand how Java communicates with your machine.
* Begin thinking like a software engineer.
  These basics also make it easier to learn advanced Java concepts later and transition to other languages.

---

## Week 1 Concepts & Notes

### Java Setup

* Install the **Java Development Kit (JDK)**.

* Use **Command Line (CLI)** to compile and run Java programs:

  ```bash
  javac HelloWorld.java
  java HelloWorld
  ```

* Use an **IDE like IntelliJ** for easier development.

### Your First Java Program

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}
```

* `public static void main(String[] args)` is the program entry point.
* `System.out.println()` prints to the console.

### Comments

```java
// This is a single-line comment

/* This is
   a multi-line comment */
```

### Primitive Data Types

| Type      | Description       | Example                   |
| --------- | ----------------- | ------------------------- |
| `int`     | Integer numbers   | `int x = 10;`             |
| `double`  | Decimal numbers   | `double y = 3.14;`        |
| `boolean` | True/False values | `boolean isTrue = false;` |
| `char`    | Single characters | `char letter = 'A';`      |

### Variables

```java
int age = 30;
double price = 19.99;
char grade = 'A';
boolean isValid = true;
```

### Type Casting

```java
int a = 10;
double b = a;         // implicit casting
int c = (int) b;      // explicit casting
```

### Input & Output

```java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your name: ");
        String name = scanner.nextLine();
        System.out.println("Hello, " + name);
    }
}
```

### Operators

#### Arithmetic Operators

```java
int x = 10 + 5;    // 15
int y = 10 - 3;    // 7
int z = 2 * 3;     // 6
int a = 10 / 2;    // 5
int b = 10 % 3;    // 1 (remainder)
```

#### Relational Operators

```java
int a = 5;
int b = 10;
boolean result = a < b;   // true
```

#### Logical Operators

```java
true && false   // false
true || false   // true
!true           // false
```

---

### Conditional Statements

```java
int score = 85;

if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else {
    System.out.println("C or below");
}
```

#### switch Statement

```java
int day = 3;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Other day");
}
```

---

## Quiz Questions

1. **What is the correct entry point for a Java program?**
Main method
2. **What command is used to print output in Java?**
System.out.println();
3. **What is the size of an `int` in Java?**
32 bits
4. **What are four common primitive data types in Java?**
Boolean, int, long, char, byte, short, float, double
5. **What is type casting in Java?**
going from one data type to another 
6. **What are the arithmetic operators in Java?**
+, -, /, *, %
7. **What is the result of casting `double d = 9.8; int i = (int) d;`?**
9
8. **Which class do we use to get user input from the console?**
Scanner class
9. **What is the difference between == and = in Java?**
== Equality operator, = Assignment operator
10. **What does `System.out.println(5 > 3 && 2 < 1);` print?**
will not compile since both have to be true
---

## Coding Challenges

> Each of these includes instructions to guide the student through incremental thinking.

1. **Number Comparison**
   Ask the user to enter two numbers. Print which number is greater or if they are equal.
```java 
int num1 = 21; 
int num2 = 17; 

if (num1 >= num2) {
    System.out.println("num1 is the larger number");
} else {
    System.out.println("num2 is small number")
}
```
2. **Basic Calculator**
   Write a program that adds two integers and prints the result.
   *Stretch:* Use `Scanner` to allow user input.
```java
Scanner scan = new Scanner(System.in);
        System.out.println("Enter a number: ");
        int num1 = scan.nextInt();
        System.out.println("Enter a number: ");
        int num2 = scan.nextInt();
        int sum = num1 + num2;
        System.out.println("sum is " + sum);
```
3. **Data Types Practice**
   Declare variables of each primitive type and print them.
```java
int number = 12;
System.out.println(number);
long longNumber = 123456434342L;
System.out.println(longNumber);
byte byteNumber = 127;
System.out.println(byteNumber);
short shortNumber = 23;
System.out.println(shortNumber);
boolean result = true;
System.out.println(result);
char character = 'p';
System.out.println(character);
float floatNumber = 1.33F;
System.out.println(floatNumber);
double doubleNumber = 29.99;
System.out.println(doubleNumber);
```
4. **Type Casting Demo**
   Demonstrate implicit and explicit casting between `int` and `double`.
```java
int n = 11;
double d = n;

double nd = 10.2;
int ni = (int)nd;
```
5. **Grade Categorizer**
   Ask the user for a numeric score and print the letter grade using `if-else`.
```java
class Scratch {
    public static void main(String[] args) {
        Scanner scan =new Scanner(System.in);

        System.out.println("Enter score");
        int score = scan.nextInt();

        char grade;

        if (score >= 90) {
            System.out.println(grade = 'A');
        }  else if (score >= 80) {
            System.out.println(grade = 'B');
        }   else if (score >= 70) {
            System.out.println(grade = 'C');
        }   else if (score >= 60) {
            System.out.println(grade = 'D');
        } else  {
            System.out.println(grade = 'E');
        }
    }
}
```
6. **Character Math**
   Assign a `char` variable, cast it to an `int`, and print both.
   *Stretch:* Try adding 1 to the char and print the result.
```java
char c = 'p';
int n = (int) c + 1;
System.out.println("n is " + n);
```

---

## Week 1 Summary

* Installed Java and set up your dev environment.
* Wrote and ran your first Java program.
* Practiced with primitive types, variables, and console I/O.
* Learned type casting and Scanner input.
* Learned how to use Java’s operators and conditional logic.
* Built confidence with foundational Java tools.
* Push to GitHub every single day you write a line of code

---

## For Next Week

### Reading 
* https://codingnomads.com/course/java-programming-101
    * Section 2) Tools of the Developer Trade
    * Section 3) Java Virtual Machine (JVM)
    * Section 4) Java's Primitive Data Types
    * Section 5) Java Variables
    * Section 6) Java Operators

### Assignments (in IntelliJ)

First:
* Make sure you have your [dev workspace setup](https://codingnomads.com/java-101-development-workspace)
* Download or clone (ideally) the [Java Lab Exercises](https://codingnomads.com/java-101-get-your-java-labs-project)

Then, complete the following exercises:
* src/labs_examples/fundamentals/labs -> exercises 3, 4, and 5
* src/labs_examples/datatypes_operators/labs -> all exercises