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
static members are associated with the blueprint (the class) rather than with individual creations 
(objects) made from that blueprint. This allows for shared resources, utility functions, 
and initialization logic that applies to the class as a whole.
2. **Can a static method access instance variables directly?**
No, a static method in Java cannot directly access instance variables of the class it belongs to; can access 
through object reference.
3. **What is the purpose of using packages?**
Allows organizing code, avoid naming conflicts, control access, promote code reusability, 
improve maintainability.
- public -
- private - 
- protected -  
- default - no access modifier provided

4. **Which statement is correct?**
   a) `object.staticMethod()`
   b) `ClassName.staticMethod()` - B

5. **What is one benefit of modular code?**
Enhanced reusability
6. **What keyword is used to define a package at the top of a file?**
package
---

## Coding Challenges

1. **Static Utility Method**
   Create a class `MathUtil` with a static method `cube(int x)` that returns the cube of a number.
```java
class MathUtil {

    public static int cube(int x) {
        return x * x * x;
    }
    public static void main(String[] args) {
        int num = 4;
        int result = MathUtil.cube(num);
        System.out.println(result);
    }
}
```
2. **Static Counter**
   Create a class `User` with a static field `userCount`. Increment the counter every time a new user is created.
```java
class User {
        private static int userCount = 0;

        public User() {
            userCount++;
        }

    public static int getUserCount() {
        return userCount;
    }

    public static void main(String[] args) {
        System.out.println("User Not Created " + User.getUserCount());
        User user1 = new User();
        System.out.println("User " + User.getUserCount());
        User user2 = new User();
        System.out.println("User " + User.getUserCount());
    }
}
```

3. **Basic Package Structure**
   Create a package `tools` and define a `Printer` class with a method `printMessage(String msg)`.
```java
package tools;

public class Printer {
    public void printMessage(String msg) {
        System.out.println("Print: " + msg);
    }
}

import tools.printer;

public class Controller {
    public static void main(String[] args) {
        Printer remotePrinter = new Printer();
        remotePrinter.printMessage("Print from printMessage method");
    }
}

```

4. **Multi-Class Architecture**
   Create a `Person` class and a separate `PersonApp` class that creates and uses `Person` objects.
```java
class Person {

    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if (age >= 0) {
            this.age = age;
        } else {
            System.out.println("Age is not set correctly");
        }
    }

    public void Intro() {
        System.out.println("Hi my name is " + name + " and I am " + age + " years old.");
    }
}

class PersonApp {
    public static void main(String[] args) {
        Person person1 = new Person("Jim", 32);
        person1.Intro();
        Person person2 = new Person("Larry", 35);
        person2.Intro();
    }
}
```
5. **Static vs Instance Demo**
   Demonstrate how static and instance fields behave differently across multiple objects.

instance field -- private String color.

- belongs to individuals objects; each object can have its own field of objects
- seperate copies exist, so changes to one object's color do not affect others
- instance fields are stored with the object in the heap memory
- accessed via an object reference - car1.getColor()

static field -- private static int numberOfCars = 0;

- Belongs to the Car class itself, not to any specific Car object
- There is only one numberOfCars field, which all Car objects share
- Static fields are stored in the method area of the class and persist for the life of the class, 
not just an individual object.
- Accessed using the class name - Car.getNumberOfCars()

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