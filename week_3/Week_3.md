# Week 3 – Java Methods, Classes & Objects

---

## Why Learn This?

Understanding methods, classes, and objects is the gateway to writing modular, maintainable, and scalable programs. This week’s topics form the backbone of object-oriented programming (OOP), which powers most modern software systems—from banking systems to Android apps.

---

## Week 3 Concepts & Notes

### Methods

A method is a block of reusable code that performs a specific task.

```java
public static void greet() {
    System.out.println("Hello!");
}

public static void main(String[] args) {
    greet();
}
```

#### Method with Parameters and Return

```java
public static int add(int a, int b) {
    return a + b;
}
```

### Method Overloading

Methods with the same name but different parameter lists.

```java
public static int square(int x) {
    return x * x;
}

public static double square(double x) {
    return x * x;
}
```

---

### Classes and Objects

A class is a blueprint; an object is a concrete instance of that class.

#### Define a Class

```java
public class Dog {
    String name;
    int age;

    public void bark() {
        System.out.println(name + " says: Woof!");
    }
}
```

#### Create an Object

```java
public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.name = "Fido";
        myDog.age = 3;
        myDog.bark();
    }
}
```

---

### Constructors

Special methods used to initialize objects.

```java
public class Dog {
    String name;
    int age;

    public Dog(String n, int a) {
        name = n;
        age = a;
    }
}
```

---

### Instance Variables vs Local Variables

* **Instance variables** are declared in the class, accessible throughout the object.
* **Local variables** exist only inside methods.

---

## Quiz Questions

1. **What is a method in Java?**
   method is a block of code designed to perform a specific task or set of actions
2. **How do you return a value from a method?**
   the return keyword is used, followed by the value to be returned
3. **What is the difference between a class and an object?**
   a class is a blueprint or template for creating objects, while an object is a specific instance of a class
4. **Which keyword is used to define a constructor?**
    same name as a class, no return type, no void, new keyword is used to create an instance of a class which then calls
    the constructor to initialize the object
5. **What is method overloading?**
    a feature where multiple methods within same class can have same name but different parameters
6. **What happens if you forget to call a constructor?**
    a Java automatically provides a default no-argument constructor 
---

## Coding Challenges

1. **Simple Adder Method**
   Write a method `add(int a, int b)` that returns the sum.
```java
public class adder {
    
    public static int add(int a, int b) {
        return a + b;
    }
    
    public static void main(String[] args) {
     int a = 11;
     int b = 7;
     
     int sum = add(a, b);
    System.out.println(sum);
    }
}

```

2. **Greeting Generator**
   Create a method `greet(String name)` that prints a personalized message.
```java
class Scratch {
    public static String greet() {
        return "Greetings my fellow coders";
    }

    public static void main(String[] args) {
        String greeter = greet();
        System.out.println(greeter);
    }
}
```
3. **Rectangle Class**
   Create a `Rectangle` class with `width` and `height` attributes and a method `area()` that returns the area.
```java
class Rectangle {
    double width;
    double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    public double area() {
        return width * height;
    }

    public static void main(String[] args) {
        Rectangle rect = new Rectangle(12.4, 5.6);

        System.out.println(rect.area());
    }
}
```

4. **Constructor Practice**
   Add a constructor to the `Rectangle` class to initialize width and height.
```java
public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
```
5. **Object Array**
   Create an array of `Rectangle` objects and print the area for each.
```java
class Scratch {

   private double width;
   private double height;

    public Scratch(double width, double height) {
        this.width = width;
        this.height = height;
    }

    public double area() {
        return width * height;
    }

    public static void main(String[] args) {

        Scratch[] rectangles = new Scratch[3];

        rectangles[0] = new Scratch(5, 9);
        rectangles[1] = new Scratch(4, 7);
        rectangles[2] = new Scratch(2, 7);

        for (int i = 0; i < rectangles.length; i++) {
            System.out.println(i + 1 + rectangles[i].area());

        }
    }
}
```

6. **Overloaded Methods**
   Create overloaded methods named `describe()` that print details for either a `String` or an `int`.
```java
class Scratch {

    public int describe(int num) {
       return num;
   }

   public String describe(String name) {
        return name;
   }

    public static void main(String[] args) {
        Scratch o = new Scratch();

        System.out.println(o.describe("Jim"));
        System.out.println(o.describe(17));
    }
}
```
---

## Week 3 Summary

* Created methods to structure code logically and reuse functionality.
* Learned to define and use classes and instantiate objects.
* Explored constructors for initializing object state.
* Practiced method overloading to create flexible APIs.
* Used object arrays to manage multiple instances of user-defined types.

---

## For Next Week

### Reading 
* https://codingnomads.com/course/java-programming-201
    * Section 1) Getting Started
    * Section 2) Java Classes - A Blueprint For Objects
    * Section 3) Java Methods
    * Section 4) Java Objects

### Assignments (in IntelliJ)

Complete the following exercises -- you can, of course, do them all:

* src/labs_examples/objects_classes_methods/labs/methods -> exercises 1 & 2
* src/labs_examples/objects_classes_methods/labs/objects -> exercises 1-5