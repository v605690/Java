# Week 5 – Static, Packages, and Project Modularity

---

## Why Learn This?

As your programs grow in size and complexity, you need ways to organize your code. This week focuses on:

* Understanding the use of `static` vs instance members.
* Structuring projects using **packages**.
* Designing modular, maintainable codebases.
  These concepts are essential for working on large-scale Java applications and collaborating with other developers.

---

## Week 5 Concepts & Notes

### The `static` Keyword

* **Static fields** and **methods** belong to the class, not individual objects.
* Access using the class name.

```java
public class MathUtils {
    public static int square(int x) {
        return x * x;
    }
}

int result = MathUtils.square(5);  // 25
```

#### Static Variables

```java
public class Counter {
    static int count = 0;

    public Counter() {
        count++;
    }
}
```

Each time you create a new `Counter` object, the shared `count` increases.

---

### Static vs Instance

| Feature      | Static                    | Instance                 |
| ------------ | ------------------------- | ------------------------ |
| Belongs to   | Class                     | Object                   |
| Accessed by  | ClassName.method()        | object.method()          |
| Memory usage | Shared across all objects | Separate copy per object |

---

### Packages

Packages are used to group related classes together.

```java
package com.codingnomads.utils;

public class MathHelper {
    public static int doubleIt(int x) {
        return x * 2;
    }
}
```

To use the class in another file:

```java
import com.codingnomads.utils.MathHelper;

public class Main {
    public static void main(String[] args) {
        System.out.println(MathHelper.doubleIt(10));
    }
}
```

---

### Project Modularity

**Modular Design Principles:**

* Break code into **cohesive components**.
* Separate concerns using packages and multi-class architecture.
* Minimize **coupling**, maximize **cohesion**.

#### Example Structure:

```
project/
├── main/
│   ├── App.java
│   ├── models/
│   │   └── User.java
│   └── utils/
│       └── Validator.java
```

Use `package` and `import` statements to reference files.

---

## Quiz Questions

1. **What does `static` mean in Java?**

2. **Can a static method access instance variables directly?**

3. **What is the purpose of using packages?**

4. **Which statement is correct?**
   a) `object.staticMethod()`
   b) `ClassName.staticMethod()`

5. **What is one benefit of modular code?**

6. **What keyword is used to define a package at the top of a file?**

---

## Coding Challenges

1. **Static Utility Method**
   Create a class `MathUtil` with a static method `cube(int x)` that returns the cube of a number.

2. **Static Counter**
   Create a class `User` with a static field `userCount`. Increment the counter every time a new user is created.

3. **Basic Package Structure**
   Create a package `tools` and define a `Printer` class with a method `printMessage(String msg)`.

4. **Multi-Class Architecture**
   Create a `Person` class and a separate `PersonApp` class that creates and uses `Person` objects.

5. **Static vs Instance Demo**
   Demonstrate how static and instance fields behave differently across multiple objects.

6. **Modular Calculator Project**
   Create a modular calculator project:

   * `Calculator.java` in `core` package
   * `InputHandler.java` in `io` package
   * `Main.java` in root or `app` package

---

## Week 5 Summary

* Used the `static` keyword to define class-level fields and methods.
* Practiced separating instance and static logic.
* Created packages and structured multi-file projects.
* Developed modular project structures to support clean architecture.

---

## For Next Week

### Reading 
* https://codingnomads.com/course/java-programming-201
    * Section 6) Static vs. Non-Static
    * Section 7) Packages

### Assignments (in IntelliJ)

Complete the following exercises -- you can, of course, do them all:

* src/labs_examples/static_nonstatic/labs -> exercises 1 & 2
* src/labs_examples/packages/labs -> PackagesExercise_01