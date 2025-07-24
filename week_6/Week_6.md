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
An **exception** in Java is an event that occurs during the execution of a program that disrupts 
the normal flow of the program's instructions. It represents an error or unexpected condition 
that arises at runtime.

2. **What block is always executed regardless of an exception?**
The **`finally` block** is always executed regardless of whether an exception occurs or not.

3. **How do you define a custom exception?**
To define a custom exception in Java, you create a class that **extends** either the `Exception`
class (for checked exceptions) or class (for unchecked exceptions). `RuntimeException`

4. **Which classes are used for reading text files line by line?**
The main classes used for reading text files line by line in Java are
BufferedReader, Scanner, Try-With-Resources

- **BufferedReader**: Most efficient for large files, provides method `readLine()`
- **Scanner**: More flexible, can parse different data types
- **Files.readAllLines()**: Loads entire file into memory at once
- **Files.lines()**: Memory efficient with Stream API support
- **Try-with-resources**: Automatically closes file resources

**BufferedReader with FileReader** is the most commonly used combination for reading text files line by line due to 
its efficiency and simplicity.

5. **What does `<T>` represent in a generic class?**
represents a **type parameter** in a generic class. It's a placeholder for an actual data type that will be 
specified when the class is instantiated. `<T>`

- **T** stands for "Type" (by convention)
- It's a **generic type parameter** that allows the class to work with different data types
- The actual type is determined when you create an instance of the class


6. **Can generics be used with primitive types like `int`?**
**No, generics cannot be used directly with primitive types like
`int`, `double`, `boolean`, etc.** 
Generics only work with **reference types** (objects).

-| Primitive | Wrapper Class |
| --- | --- |
| `int` | `Integer` |
| `double` | `Double` |
| `float` | `Float` |
| `long` | `Long` |
| `short` | `Short` |
| `byte` | `Byte` |
| `char` | `Character` |
| `boolean` | `Boolean` |


## Coding Challenges

1. **Division with Exception Handling**
   Write a program that takes two integers and divides them. Catch division by zero.
```java
public class FinallyExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0; // This will throw ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Caught exception: " + e.getMessage());
        } finally {
            System.out.println("Finally block executed - cleanup complete");
        }
    }
}
```
2. **Write to a File**
   Prompt the user for input and save it to a text file.
```java
class Scratch {
    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter your message: ");
        String message = scanner.nextLine();
        
        try (FileWriter writer = new FileWriter("output.txt")){
            writer.write(message);
            System.out.println("Message saved to output.txt");
        } catch (IOException e) {
            System.out.println("Error saving file: " + e.getMessage());
        }
        scanner.close();

        try (BufferedReader reader = new BufferedReader(new FileReader("output.txt"))) {
            String line;
            System.out.println("Contents of output.txt");
            System.out.println("-----------------------");

            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
        scanner.close();
    } 
}
```

3. **Read from a File**
   Read and print the contents of the file created in Challenge 2.
Added in exercise 2 example

4. **Custom Exception for Age Check**
   Throw a custom exception if a user is under 18.
```java
class UnderageException extends Exception {
    public UnderageException(String message) {
        super(message);
    }
}

class SimpleAgeCheck {
    public static void checkAge(int age) throws UnderageException {
        if (age < 18) {
            throw new UnderageException("User must be 18 or older. Current age: " + 18);
        }
    }

    public static void main(String[] args) {

        try {
            checkAge(18);
            System.out.println("User is old enough!");
        } catch (UnderageException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```
5. **Generic Container**
   Create a generic class `Container<T>` with methods to store and retrieve a value.
```java
class Scratch {

    public static void main(String[] args) {
        Container<String> stringContainer = new Container<>();
        stringContainer.setValue("15 2TB Sata III Drives");
        System.out.println("String value: " + stringContainer.getValue());

        Container<Integer> intContainer = new Container<>(47);
        System.out.println("Integer value: " + intContainer.getValue());

        Container<Double> doubleContainer = new Container<>();
        doubleContainer.setValue(3.14159);
        System.out.println("Double value: " + doubleContainer.getValue());

        Container<String> emptyContainer = new Container<>();
        System.out.println("Is empty: " + emptyContainer.isEmpty());

        emptyContainer.setValue("Container not empty");
        System.out.println("Is empty: " + emptyContainer.isEmpty());
    }
}

class Container<T> {
    private T value;

    public Container() {
        this.value = null;
    }

    public Container(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }

    public void setValue(T value) {
        this.value = value;
    }

    public boolean isEmpty() {
        return value == null;
    }

    public void clear() {
        this.value = null;
    }

    @Override
    public String toString() {
        return "Container{" +
                "value=" + value +
                '}';
    }
}
```
6. **Generic Sum Calculator**
   Create a generic method `sum` that takes two numbers and returns their sum.
```java
class Scratch {

    public static <T extends Number> double sum(T x, T y) {
        return x.doubleValue() + y.doubleValue();
    }

    public static void main(String[] args) {

        System.out.println("Integer Sum: " + sum(3, 5));
        System.out.println("Float Sum: " + sum(1.5f, 3.5f));

    }
}
```
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