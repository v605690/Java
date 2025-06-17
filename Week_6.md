# Week 6 – Exception Handling, File I/O, & Generics

---

## Why Learn This?

Robust applications must handle errors gracefully, read and write files, and work flexibly with different data types. This week you’ll learn to:

* Use Java’s exception handling model.
* Perform file operations for data persistence.
* Use generics to write flexible, type-safe code.
  These skills are essential for building real-world applications and backend services.

---

## Week 6 Concepts & Notes

### Exception Handling

Exceptions help manage runtime errors in a controlled manner.

#### Basic try-catch

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

#### try-catch-finally

```java
try {
    // code that might throw
} catch (Exception e) {
    // handle it
} finally {
    // always runs
}
```

#### Multiple Catch Blocks

```java
try {
    String s = null;
    System.out.println(s.length());
} catch (NullPointerException e) {
    System.out.println("Null value");
} catch (Exception e) {
    System.out.println("Some error");
}
```

---

### Custom Exceptions

```java
public class MyException extends Exception {
    public MyException(String message) {
        super(message);
    }
}
```

---

### File I/O

#### Writing to a File

```java
import java.io.FileWriter;
import java.io.IOException;

public class WriteFile {
    public static void main(String[] args) {
        try (FileWriter writer = new FileWriter("output.txt")) {
            writer.write("Hello, file!");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

#### Reading from a File

```java
import java.io.BufferedReader;
import java.io.FileReader;

public class ReadFile {
    public static void main(String[] args) {
        try (BufferedReader reader = new BufferedReader(new FileReader("output.txt"))) {
            String line;
            while ((line = reader.readLine()) != null)
                System.out.println(line);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

### Generics

Allow type-safe operations without committing to a specific type at compile time.

```java
public class Box<T> {
    private T item;

    public void set(T item) {
        this.item = item;
    }

    public T get() {
        return item;
    }
}
```

Usage:

```java
Box<String> stringBox = new Box<>();
stringBox.set("Java");
System.out.println(stringBox.get());
```

---

## Quiz Questions

1. **What is an exception in Java?**

2. **What block is always executed regardless of an exception?**

3. **How do you define a custom exception?**

4. **Which classes are used for reading text files line by line?**

5. **What does `<T>` represent in a generic class?**

6. **Can generics be used with primitive types like `int`?**

---

## Coding Challenges

1. **Division with Exception Handling**
   Write a program that takes two integers and divides them. Catch division by zero.

2. **Write to a File**
   Prompt the user for input and save it to a text file.

3. **Read from a File**
   Read and print the contents of the file created in Challenge 2.

4. **Custom Exception for Age Check**
   Throw a custom exception if a user is under 18.

5. **Generic Container**
   Create a generic class `Container<T>` with methods to store and retrieve a value.

6. **Generic Sum Calculator**
   Create a generic method `sum` that takes two numbers and returns their sum.

---

## Week 6 Summary

* Used try-catch blocks and custom exceptions to manage program errors.
* Read and wrote files using Java I/O classes.
* Wrote generic classes and methods for flexible and type-safe programming.
* Practiced building real-world tools like file readers and calculators.

---

## For Next Week

### Reading 
* https://codingnomads.com/course/java-programming-301
    * Section 1) Getting Started
    * Section 2) Exception Handling
    * Section 3) Input / Output (I/O)
    * Section 5) Generics

### Assignments (in IntelliJ)

Complete the following exercises -- you can, of course, do them all:

* src/labs_examples/exception_handling/labs -> exercises 1-7
* src/labs_examples/input_output/labs -> exercises 2 & 4 