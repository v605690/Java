# Week 9 – Data Structures, Algorithms & Capstone Planning

---

## Why Learn This?

Data structures and algorithms are essential for solving real-world problems efficiently. In this final week, you’ll:

* Review Java’s core data structures.
* Understand algorithm basics like sorting and searching.
* Begin planning and designing your capstone project.
  Mastering these topics improves your ability to write optimized, interview-ready code and architect complete applications.

---

## Week 9 Concepts & Notes

### Data Structures in Java

#### Lists

```java
import java.util.ArrayList;
List<String> names = new ArrayList<>();
names.add("Alice");
```

#### Stacks

```java
import java.util.Stack;
Stack<Integer> stack = new Stack<>();
stack.push(10);
int top = stack.pop();
```

#### Queues

```java
import java.util.LinkedList;
Queue<String> queue = new LinkedList<>();
queue.add("first");
String head = queue.poll();
```

#### Maps

```java
import java.util.HashMap;
Map<String, Integer> map = new HashMap<>();
map.put("Alice", 25);
int age = map.get("Alice");
```

#### Sets

```java
import java.util.HashSet;
Set<String> set = new HashSet<>();
set.add("Java");
boolean hasJava = set.contains("Java");
```

---

### Algorithm Basics

#### Sorting: Bubble Sort

```java
public static void bubbleSort(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++) {
        for (int j = 0; j < arr.length - 1 - i; j++) {
            if (arr[j] > arr[j+1]) {
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
}
```

#### Searching: Linear Search

```java
public static int linearSearch(int[] arr, int key) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == key) return i;
    }
    return -1;
}
```

#### Time Complexity

| Operation        | Time Complexity |
| ---------------- | --------------- |
| Access in Array  | O(1)            |
| Search in List   | O(n)            |
| HashMap Lookup   | O(1)            |
| Sorting (Bubble) | O(n²)           |

---

### Capstone Project Planning

#### Project Requirements

* **Use Java OOP** (classes, constructors, encapsulation)
* **Integrate JDBC + SQL**
* **Include file I/O or data persistence**
* **Demonstrate modular structure (multi-class project)**

#### Project Ideas

* Inventory Management System
* Personal Finance Tracker
* Task or Habit Tracker
* Student Database Application
* Note-Taking App with File Storage

#### Capstone Checklist

* [ ] Defined project idea and features
* [ ] Setup project structure and packages
* [ ] Implement core functionality
* [ ] Connect database and manage data
* [ ] Add user interaction (console input or file input)
* [ ] Document code and write a README

---

## Quiz Questions

1. **Which data structure uses LIFO (Last In First Out)?**

2. **What does `queue.poll()` do?**

3. **Which data structure guarantees unique values?**

4. **What’s the time complexity of a HashMap `get()` call?**

5. **What does a `Map` store?**

6. **What is the primary purpose of the capstone project?**

---

## Coding Challenges

1. **Stack Reverser**
   Push letters of a word onto a stack and print the reversed word by popping.

2. **Queue Simulation**
   Simulate a basic print queue: add names to queue, then process them.

3. **Frequency Counter**
   Count the frequency of words in a sentence using a `Map<String, Integer>`.

4. **Duplicate Remover**
   Use a `Set` to remove duplicates from a list of integers.

5. **Bubble Sort Practice**
   Write and test your own implementation of bubble sort.

6. **Capstone Scaffolding**
   Create a new project with packages: `models`, `db`, and `app`. Add basic starter classes.

---

## Week 9 Summary

* Reviewed Java’s key data structures and when to use each.
* Practiced sorting, searching, and analyzing time complexity.
* Designed the architecture for your capstone project.
* Set up a modular structure and prepared to integrate all your skills.

---

## Moving forward
* Don't stop practicing! 
* Finish all the exercises you weren't able to complete earlier
* Finish the curriculum on codingnomads.com Java 101, 201, and 301
* Finish the remaining labs that were not assigned to you in the summer session
* Stay in touch! We're still here to help!