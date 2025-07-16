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
Encapsulation means that a class acts as a container, holding both its data members (fields/variables) 
and the methods that manipulate those data members. A crucial aspect of encapsulation is making the data members of a 
class private
2. **What does `extends` mean in a class declaration?**
Is a keyword primarily used to establish an inheritance relationship between two classes or interfaces.
3. **What is method overriding?** 
Subclass provides a specific implementation of a method already defined in its superclass. 
This specific implementation replaces the default behavior inherited from the superclass.
4. **What is an abstract class?**
Is a class declared with the abstract keyword. It serves as a blueprint for other classes, 
defining common behaviors and characteristics that can be shared among multiple related classes
5. **How do you call a superclass constructor?**
A superclass constructor is called from a subclass constructor using the super() keyword. 
This call must be the first statement within the subclass constructor.
6. **What’s the difference between `this` and `super`?**
this refers to the current instance
super refers to the parent class
---

## Coding Challenges

1. **Encapsulated Student**
   Create a `Student` class with `name` and `gpa` as private fields. Provide public getter and setter methods.
```java
class Student {
   private String name;
   private int gpa;

   public String getName() {
      return name;
   }

   public void setName(String name) {
      this.name = name;
   }

   public int getGpa() {
      return gpa;
   }

   public void setGpa(int gpa) {
      this.gpa = gpa;
   }
}
```
2. **Inheritance Practice**
   Create a base class `Vehicle` with a method `move()`. Derive a `Car` class that adds a `drive()` method.
```java
class Vehicle {
    public void move() {
        System.out.println("We are moving...");
    }
}

class Car extends Vehicle {
    public void drive() {
        System.out.println("Finally, we are driving to our new place....");
    }

    public static void main(String[] args) {

        Car car = new Car();

        car.move();
        car.drive();

    }
}
```
3. **Method Overriding**
   Create a superclass `Employee` with a `work()` method. Subclass `Developer` overrides `work()` with a different message.
```java
class Employee {
    public void work() {
        System.out.println("Perform work operation");
    }
}

class Developer extends Employee {
    @Override
    public void work() {
        System.out.println("Develop a Java e-commerce app");
    }

    public static void main(String[] args) {
        Employee employee = new Developer();
        employee.work();
    }
}
```
4. **Abstract Shape**
   Create an abstract class `Shape` with an abstract method `area()`. Implement it in a `Rectangle` subclass.
```java
class Rectangle extends Shape {
   double length;
   double width;

   public Rectangle(double length, double width) {
      this.length = length;
      this.width = width;
   }

   @Override
   public double area() {
      return length * width;
   }

   public static void main(String[] args) {

      Rectangle rectangle = new Rectangle(33, 13);
      double r = rectangle.area();
      System.out.println(r);
   }
}
```
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
