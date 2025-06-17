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

2. **Even or Odd Loop**
   Print whether each number from 1 to 20 is even or odd using a `for` loop.

3. **Sum of Array**
   Create an array of integers and print the total sum.

4. **Favorite Foods List**
   Create an `ArrayList<String>` to store three of your favorite foods. Print them out one per line.

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
