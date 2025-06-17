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

2. **What keyword is used to make a method thread-safe?**

3. **What is a lambda expression?**

4. **Which interface would you use to evaluate a condition?**

5. **What is the output of `() -> System.out.println("Hi")`?**

6. **What is the purpose of method references like `System.out::println`?**

---

## Coding Challenges

1. **Simple Thread**
   Create a thread that prints numbers 1 to 5 with a delay of 1 second between each.

2. **Runnable Calculator**
   Implement a `Runnable` that takes two integers and prints their sum.

3. **Thread Synchronization**
   Write a class that increments a shared counter using multiple threads, using synchronization to avoid errors.

4. **Lambda Greeting**
   Create a `Greeting` interface and use a lambda to implement it.

5. **Functional Filter**
   Create a list of integers and use a `Predicate` with `removeIf()` to remove odd numbers.

6. **Method Reference Logger**
   Create a static method `log(String msg)` and use a method reference to pass it as a `Consumer<String>`.

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