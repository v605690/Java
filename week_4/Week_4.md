# Week 4 – Core OOP Concepts

---

## Why Learn This?

Object-Oriented Programming (OOP) enables you to write scalable, reusable, and maintainable software. Understanding the pillars of OOP—encapsulation, inheritance, polymorphism, and abstraction—will help you design software that mirrors real-world systems, reduces redundancy, and is easier to debug and extend.

---

## Week 4 Concepts & Notes

### What is OOP?

OOP is a programming paradigm based on the concept of "objects" that contain data and methods.

---

### Encapsulation

* **Definition:** Bundling data (variables) and methods (functions) that operate on that data within one unit (class), and restricting access to some of the object’s components.
* Use **private** access modifiers and **getter/setter** methods.

```java
public class Person {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String n) {
        name = n;
    }
}
```

---

### Inheritance

* Allows one class to inherit fields and methods from another.

```java
public class Animal {
    public void makeSound() {
        System.out.println("Some sound");
    }
}

public class Dog extends Animal {
    public void bark() {
        System.out.println("Bark");
    }
}
```

---

### Polymorphism

* **Method Overriding:** Subclass provides a specific implementation of a method already defined in its superclass.

```java
public class Animal {
    public void speak() {
        System.out.println("Generic sound");
    }
}

public class Cat extends Animal {
    @Override
    public void speak() {
        System.out.println("Meow");
    }
}
```

* **Dynamic Method Dispatch:** The type of object determines which overridden method is called at runtime.

---

### Abstraction

* **Definition:** Hiding implementation details and showing only essential features.
* Achieved with **abstract classes** or **interfaces**.

```java
public abstract class Shape {
    public abstract double area();
}

public class Circle extends Shape {
    double radius;

    public Circle(double r) {
        radius = r;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}
```

---

### `this`, `super`, and Constructor Chaining

* `this` refers to the current instance.
* `super` refers to the parent class.
* Use constructor chaining to avoid duplicate initialization logic.

```java
public class Employee {
    String name;

    public Employee(String name) {
        this.name = name;
    }
}

public class Manager extends Employee {
    public Manager(String name) {
        super(name); // constructor chaining
    }
}
```

---

## Quiz Questions

1. **What is encapsulation?**

2. **What does `extends` mean in a class declaration?**

3. **What is method overriding?**

4. **What is an abstract class?**

5. **How do you call a superclass constructor?**

6. **What’s the difference between `this` and `super`?**

---

## Coding Challenges

1. **Encapsulated Student**
   Create a `Student` class with `name` and `gpa` as private fields. Provide public getter and setter methods.

2. **Inheritance Practice**
   Create a base class `Vehicle` with a method `move()`. Derive a `Car` class that adds a `drive()` method.

3. **Method Overriding**
   Create a superclass `Employee` with a `work()` method. Subclass `Developer` overrides `work()` with a different message.

4. **Abstract Shape**
   Create an abstract class `Shape` with an abstract method `area()`. Implement it in a `Rectangle` subclass.

5. **Constructor Chaining**
   Create a class hierarchy `Person -> Student` where the `Student` constructor calls the `Person` constructor.

6. **Polymorphism in Action**
   Create an array of `Animal` objects containing `Dog` and `Cat` subclasses. Loop through the array and call `speak()` on each.

---

## Week 4 Summary

* Practiced the four core principles of Object-Oriented Programming: encapsulation, inheritance, polymorphism, and abstraction.
* Used constructors and keywords like `this` and `super` to manage object relationships and hierarchies.
* Built reusable and extendable class structures.
* Applied OOP to real-world modeling problems.

---

## For Next Week

### Reading 
* https://codingnomads.com/course/java-programming-201
    * Section 5) Object-Oriented Programming

### Assignments (in IntelliJ)

Complete the following exercises -- you can, of course, do them all:

* src/labs_examples/objects_classes_methods/labs/oop/A_inheritance -> exercises 1-5
* src/labs_examples/objects_classes_methods/labs/oop/B_polymorphism -> exercise 1

**Stretch Goal:** 
* src/labs_examples/objects_classes_methods/labs/oop/C_blackjack -> exercises 1-4
