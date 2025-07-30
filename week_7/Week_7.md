# Week 7 – Multithreading & Functional Java

---

## Why Learn This?

Modern applications often perform multiple tasks at once—like downloading files while updating the UI. Java's multithreading and functional programming tools help us write efficient, scalable, and cleaner code. This week you'll learn to:

* Run concurrent tasks using threads.
* Write concise code using lambda expressions.
* Use Java’s functional interfaces for cleaner APIs.

---

## Week 7 Concepts & Notes

### What is a Thread?

A thread is a lightweight unit of execution within a process. Java provides built-in support for multithreading.

---

### Creating Threads

#### 1. Extending the Thread class

```java
public class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running");
    }
}

new MyThread().start();
```

#### 2. Implementing Runnable

```java
public class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable running");
    }
}

new Thread(new MyRunnable()).start();
```

---

### Thread Lifecycle

* **New → Runnable → Running → Terminated**
* Optional: **Blocked**, **Waiting**, **Timed Waiting**

---

### Synchronization

Used to avoid thread interference and memory consistency errors.

```java
public synchronized void increment() {
    counter++;
}
```

Or use a `synchronized` block:

```java
synchronized (this) {
    // critical section
}
```

---

### Lambda Expressions

Used to create concise, anonymous implementations of functional interfaces.

```java
interface Greeting {
    void sayHello();
}

Greeting g = () -> System.out.println("Hello!");
```

---

### Functional Interfaces

An interface with exactly one abstract method.

Examples in `java.util.function`:

* `Predicate<T>`: boolean test(T t)
* `Function<T, R>`: R apply(T t)
* `Consumer<T>`: void accept(T t)
* `Supplier<T>`: T get()

---

### Method References

Shorthand for calling existing methods via lambda.

```java
public class Printer {
    public static void printMsg() {
        System.out.println("Hello");
    }
}

Runnable r = Printer::printMsg;
r.run();
```

---

## Quiz Questions

1. **What is the difference between `start()` and `run()` in a Thread?**
### method: `start()`
- **Creates a new thread** and begins its execution
- Calls the method **in the new thread** `run()`
- Can only be called **once** per thread object
- Throws if called multiple times `IllegalThreadStateException`

### method: `run()`
- Contains the **code that will be executed** when the thread runs
- If called directly, it executes **in the current thread** (not in a new thread)
- Can be called multiple times
- Is the method you **override** to define what the thread should do

2. **What keyword is used to make a method thread-safe?**
The `synchronized` keyword ensures that only one thread can execute the method at a time, 
making it thread-safe.

3. **What is a lambda expression?**
A **lambda expression** is a concise way to write anonymous functions in Java.
**Parameter list**: `()` - can be empty, single parameter, or multiple parameters
**Arrow operator**: `->` - separates parameters from the body
**Body**: The code to execute - can be a single expression or a block of statements
   (parameters) -> expression

4. **Which interface would you use to evaluate a condition?**
To evaluate a condition in Java, you would use the **`Predicate<T>`** interface.
The interface has one abstract method: `Predicate<T>`
5. 
**Purpose-built**: Specifically designed for boolean evaluations
**Composable**: Can be combined with `and()`, `or()`, and `negate()` methods
**Stream-friendly**: Works seamlessly with Stream API operations like `filter()`
**Readable**: Makes code intent clear and expressive

So whenever you need to evaluate a condition or test whether something meets certain criteria, is the go-to functional interface in Java. `Predicate<T>`

5. **What is the output of `() -> System.out.println("Hi")`?**
The lambda expression by itself produces **no output**. 
It only defines a function that, when executed, would print "Hi". 
The lambda must be assigned to a compatible functional interface 
and then invoked to actually produce the output "Hi". 
`() -> System.out.println("Hi")`

6. **What is the purpose of method references like `System.out::println`?**
Method references in Java `System.out::println` are a shorthand notation, that allow you to refer 
to methods without invoking them. They provide a more concise way to write lambda expressions 
when the lambda simply calls an existing method.

The `::` operator creates a reference to the `println` method of the `System.out` object, 
making the code more readable and concise.

---

## Coding Challenges

1. **Simple Thread**
   Create a thread that prints numbers 1 to 5 with a delay of 1 second between each.
```java
Thread t = new Thread(() -> {
    for (int i = 1; i < 5; i++){
        try {
            Thread.sleep(1000);  // 1 second delay
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("I'm in the Thread! " + i);  // Prints 0-4
    }
});
```

2. **Runnable Calculator**
   Implement a `Runnable` that takes two integers and prints their sum.
```java
public class SumRunnable implements Runnable {
    private final int num1;
    private final int num2;
    
    public SumRunnable(int num1, int num2) {
        this.num1 = num1;
        this.num2 = num2;
    }
    
    @Override
    public void run() {
        int sum = num1 + num2;
        System.out.println("Sum of " + num1 + " and " + num2 + " is: " + sum);
    }
}

public class Main {
    public static void main(String[] args) {
        // Create a Runnable that calculates sum of 5 and 3
        SumRunnable calculator = new SumRunnable(5, 3);

        // Run it in a new thread
        Thread thread = new Thread(calculator);
        thread.start();

        // Or run it directly (without threading)
        calculator.run();
    }
}
```
3. **Thread Synchronization**
   Write a class that increments a shared counter using multiple threads, using synchronization to avoid errors.
```java
public class SynchronizedCounter {
    private int counter = 0;
    
    public synchronized void increment() {
        counter++;
    }
    
    public synchronized int getValue() {
        return counter;
    }
    
    public static void main(String[] args) throws InterruptedException {
        SynchronizedCounter sharedCounter = new SynchronizedCounter();
        Thread[] threads = new Thread[5];
        
        // Create and start multiple threads
        for (int i = 0; i < threads.length; i++) {
            threads[i] = new Thread(() -> {
                for (int j = 0; j < 1000; j++) {
                    sharedCounter.increment();
                }
            });
            threads[i].start();
        }
        
        // Wait for all threads to complete
        for (Thread thread : threads) {
            thread.join();
        }
        
        System.out.println("Final counter value: " + sharedCounter.getValue());
    }
}
```
4. **Lambda Greeting**
   Create a `Greeting` interface and use a lambda to implement it.
```java
// Define the Greeting interface
interface Greeting {
    void sayHello(String name);
}

// Use a lambda expression to implement it
public class Main {
    public static void main(String[] args) {
        // Lambda implementation of the Greeting interface
        Greeting greeting = (name) -> System.out.println("Hello, " + name + "!");
        
        // Use the implementation
        greeting.sayHello("World");
    }
}
```
5. **Functional Filter**
   Create a list of integers and use a `Predicate` with `removeIf()` to remove odd numbers.
```java
import java.util.*;
import java.util.function.Predicate;

public class FilterOddNumbers {
    public static void main(String[] args) {
        // Create a list of integers
        List<Integer> numbers = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10));

        System.out.println("Original list: " + numbers);

        // Create a Predicate that tests for odd numbers
        Predicate<Integer> isOdd = n -> n % 2 != 0;

        // Use removeIf() with the predicate to remove odd numbers
        numbers.removeIf(isOdd);

        System.out.println("After removing odd numbers: " + numbers);
    }
}
```
6. **Method Reference Logger**
   Create a static method `log(String msg)` and use a method reference to pass it as a `Consumer<String>`.
```java
import java.util.function.Consumer;
import java.util.Arrays;
import java.util.List;

public class MethodReferenceLogger {
    
    // Static method that logs a message
    public static void log(String msg) {
        System.out.println("[LOG] " + msg);
    }
    
    public static void main(String[] args) {
        // Using method reference to pass the static log method as a Consumer<String>
        Consumer<String> logger = MethodReferenceLogger::log;
        
        // Test the consumer
        logger.accept("This is a test message");
        logger.accept("Application started successfully");
        
        // Demonstrate using the method reference with a collection
        List<String> messages = Arrays.asList(
            "Processing user data",
            "Database connection established", 
            "Operation completed"
        );
        
        System.out.println("\nProcessing messages:");
        messages.forEach(MethodReferenceLogger::log);  // Direct method reference
        
        // Or using the consumer variable
        System.out.println("\nUsing consumer variable:");
        messages.forEach(logger);
    }
}
```
---

## Week 7 Summary

* Created concurrent programs using threads and `Runnable`.
* Synchronized shared resources to prevent race conditions.
* Simplified code using lambda expressions and method references.
* Used functional interfaces for expressive, reusable operations.

## For Next Week

### Reading 

* https://codingnomads.com/course/java-programming-301
    * Section 4) Multithreading
    * Section 7) Lambda Expressions & Method References

### Assignments (in IntelliJ)

Complete the following exercises -- you can, of course, do them all:
* src/labs_examples/multi_threading/labs -> exercises 1-7
* src/labs_examples/lambdas/labs -> exercises 1-4 (stretch)