# Week 2 – Operators, Conditionals, Logic, Loops, Arrays, ArrayLists

---

## Why Learn This?

Control flow and data structures are essential for writing useful programs. This week, you'll learn to:

* Make decisions in code using conditionals.
* Repeat operations with loops.
* Store and manage collections of data using arrays and ArrayLists.
  These tools are used in nearly every program—from calculators to social media platforms.

---

## Week 2 Concepts & Notes

### Loops

#### for loop

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

#### while loop

```java
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```

#### do-while loop

```java
int i = 0;
do {
    System.out.println(i);
    i++;
} while (i < 5);
```

---

### Arrays

```java
int[] numbers = {10, 20, 30};
System.out.println(numbers[1]);  // 20
```

#### Iterating over arrays

```java
for (int num : numbers) {
    System.out.println(num);
}
```

---

### ArrayLists

```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");
list.remove("Apple");
System.out.println(list.size());  // 1
```

---

## Quiz Questions

1. **What does the `%` operator do?**

2. **What is the output of `while(false)`?**

3. **Which loop executes at least once, even if the condition is false?**

4. **What’s the default value of an uninitialized `int` array element?**

5. **What’s the key difference between an array and an ArrayList?**

6. **What does `break` do inside a loop or switch statement?**

---

## Coding Challenges

1. **Number Comparison**
   Ask the user to enter two numbers. Print which number is greater or if they are equal.
```java
public class NumberComparison {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in); 

        System.out.print("Enter the first number: "); 
        int number1 = input.nextInt(); 

        System.out.print("Enter the second number: ");
        int number2 = input.nextInt();

        if (number1 > number2) {
            System.out.println(number1 + " is greater than " + number2);
        } else if (number2 > number1) {
            System.out.println(number2 + " is greater than " + number1);
        } else {
            System.out.println("Both numbers are equal.");
        }

        input.close();
    }
}
```
2. **Even or Odd Loop**
   Print whether each number from 1 to 20 is even or odd using a `for` loop.
```java
public class EvenOddChecker {
    public static void main(String[] args) {
        for (int i = 1; i <= 20; i++) {
            if (i % 2 == 0) {
                System.out.println(i + " is even.");
            } else {
                System.out.println(i + " is odd.");
            }
        }
    }
}
```
3. **Sum of Array**
   Create an array of integers and print the total sum.
```java
public class ArraySum {

    public static void main(String[] args) {
        
        int[] numbers = {10, 20, 30, 40, 50};
        
        int sum = 0;
        
        for (int number : numbers) {
            sum += number; 
        }
        
        System.out.println("The total sum of the array elements is: " + sum);
    }
}
```
4. **Favorite Foods List**
   Create an `ArrayList<String>` to store three of your favorite foods. Print them out one per line.

```java
import java.util.ArrayList;

class Scratch {

    ArrayList<String> favFoods = new ArrayList<>();

    public static void main(String[] args) {
        Scratch s = new Scratch();

        s.favFoods.add("Pizza");
        s.favFoods.add("Pasta");
        s.favFoods.add("Catfish PoBoy");

        for (String f : s.favFoods) {
            System.out.println(f);
        }
    }
}
```
5. **FizzBuzz**
   Print numbers 1 through 30. For multiples of 3, print "Fizz"; for 5, print "Buzz"; for both, print "FizzBuzz".

---

## Week 2 Summary

* Practiced with loops to create repeating behavior.
* Worked with arrays and ArrayLists to manage collections of data.
* Built practical programs like calculators, graders, and FizzBuzz.

---

## For Next Week

### Reading 
* https://codingnomads.com/course/java-programming-101
    * Section 7) Conditions & Loops
    * Section 8) Arrays & ArrayLists

### Assignments (in IntelliJ)
Complete the following exercises -- you can, of course, do them all:

* src/labs_examples/conditions_loops/labs -> exercises 1-6, 8, 9, 10
* src/labs_examples/arrays/labs -> exercises 1-5
