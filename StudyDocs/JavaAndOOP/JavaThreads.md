### 1. Need for Threads in Java
**Answer:** Threads allow multiple tasks to run concurrently within a single program, improving performance and responsiveness.

**Easy to Remember:** Threads enable concurrent task execution.

### 2. Creating a Thread
**Answer:** You can create a thread by extending the `Thread` class or implementing the `Runnable` interface.

**Easy to Remember:** Two ways - extend `Thread` or implement `Runnable`.

### 3. Creating a Thread by Extending Thread Class
**Answer:** 
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running.");
    }
}
MyThread t = new MyThread();
t.start();
```

**Easy to Remember:** Extend `Thread`, override `run()`, call `start()`.

### 4. Creating a Thread by Implementing Runnable Interface
**Answer:** 
```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread is running.");
    }
}
Thread t = new Thread(new MyRunnable());
t.start();
```

**Easy to Remember:** Implement `Runnable`, pass to `Thread`, call `start()`.

### 5. Running a Thread in Java
**Answer:** Start the thread by calling its `start()` method.

**Easy to Remember:** Call `start()` to run the thread.

### 6. Different States of a Thread (Thread States (High-Level))
**Answer:** 
1. **New:** Thread is created but not started.
2. **Runnable:** Thread is ready to run.
3. **Blocked:** Thread is blocked and waiting for a [monitor lock](#28-what-is-a-monitor-lock).
4. **Waiting:** Thread is waiting indefinitely for another thread.
5. **Timed Waiting:** Thread is waiting for a specified period.
6. **Terminated:** Thread has finished execution.

**Easy to Remember:** New, Runnable, Blocked, Waiting, Timed Waiting, Terminated.

### 7. Thread Priority and Changing Priority
**Answer:** Priority determines the relative importance of a thread.
```java
thread.setPriority(Thread.MAX_PRIORITY); // Sets priority to 10
```

**Easy to Remember:** Use `setPriority()` to change thread priority.

### 8. ExecutorService
**Answer:** `ExecutorService` is a framework for managing a pool of threads.

**Easy to Remember:** Manages thread pools for concurrent execution.

### 9. Example of ExecutorService
**Answer:** 
```java
ExecutorService executor = Executors.newFixedThreadPool(5);
executor.submit(() -> System.out.println("Task executed"));
executor.shutdown();
```

**Easy to Remember:** Create pool with `Executors`, submit tasks, shutdown.

### 10. Creating Executor Services
**Answer:** 
1. **FixedThreadPool:** A fixed-size thread pool.
2. **CachedThreadPool:** Creates new threads as needed.
3. **SingleThreadExecutor:** A single worker thread.

**Easy to Remember:** Fixed, Cached, Single-thread executor services.

### 11. Checking ExecutionService Task Execution Success
**Answer:** Use `Future.get()` method.
```java
Future<String> future = executor.submit(callable);
String result = future.get(); // Checks if the task completed successfully
```

**Easy to Remember:** Use `Future.get()` to check task completion.

### 12. Callable and Executing from ExecutorService
**Answer:** 
```java
Callable<String> callable = () -> "Task result";
Future<String> future = executor.submit(callable);
String result = future.get();
```

**Easy to Remember:** Callable returns a result, use `submit(callable)`.

### 13. Synchronization of Threads
**Answer:** Ensures that only one thread accesses a resource at a time.

**Easy to Remember:** Ensures one thread access to resources.

### 14. Example of a Synchronized Block
**Answer:** 
```java
synchronized(this) {
    // synchronized code
}
```

**Easy to Remember:** Use `synchronized(this)` to create a synchronized block.

### 15. Synchronizing a Static Method
**Answer:** Yes, use the `synchronized` keyword.
```java
synchronized static void syncMethod() {
    // synchronized code
}
```

**Easy to Remember:** Use `synchronized` keyword on static method.

### 16. Use of Join Method in Threads
**Answer:** Waits for a thread to finish its execution.
```java
thread.join();
```

**Easy to Remember:** Use `join()` to wait for thread completion.

### 17. Other Important Methods in Threads
**Answer:**
1. **sleep(long millis):** Pauses the thread.
2. **yield():** Temporarily pauses the thread to allow others to execute.
3. **interrupt():** Interrupts a thread.

**Easy to Remember:** sleep, yield, interrupt.

### 18. Deadlock
**Answer:** A situation where two or more threads are blocked forever, waiting for each other.

**Easy to Remember:** Threads block each other permanently.

### 19. Important Methods for Inter-Thread Communication
**Answer:** `wait()`, `notify()`, `notifyAll()`.

**Easy to Remember:** Key methods: wait, notify, notifyAll.

### 20. Use of Wait Method
**Answer:** Causes the current thread to wait until another thread invokes `notify()` or `notifyAll()`.

**Easy to Remember:** Waits for notify/notifyAll.

### 21. Use of Notify Method
**Answer:** Wakes up a single thread waiting on the object's monitor.

**Easy to Remember:** Wakes one waiting thread.

### 22. Use of NotifyAll Method
**Answer:** Wakes up all threads waiting on the object's monitor.

**Easy to Remember:** Wakes all waiting threads.

### 23. Synchronized Program with Wait and Notify Methods
**Answer:** 
```java
class SharedResource {
    synchronized void waitMethod() throws InterruptedException {
        wait();
    }

    synchronized void notifyMethod() {
        notify();
    }
}

SharedResource resource = new SharedResource();
Thread t1 = new Thread(() -> {
    try {
        resource.waitMethod();
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
});
Thread t2 = new Thread(resource::notifyMethod);

t1.start();
t2.start();
```

**Easy to Remember:** Use `synchronized`, `wait()`, and `notify()`.

### 24. Difference Between Processes and Threads
**Answer:**
- **Processes:** Independent execution units with their own memory space. Communication between processes is more complex.
- **Threads:** Smaller units within a process that share the same memory space. Easier communication and lower overhead.

**Easy to Remember:** Processes are independent with separate memory; threads are part of a process sharing memory.


### 25. Difference Between Synchronized Method and Synchronized Block
**Answer:**
- **Synchronized Method:** Locks the entire method, affecting all the code within it.
- **Synchronized Block:** Locks only the specific block of code, allowing more fine-grained control over synchronization.

**Easy to Remember:** Method locks the entire method; block locks specific code segment.

### 26. Thread Synchronization Inside a Monitor
**Answer:** Thread synchronization in Java occurs within a monitor, which is a mechanism that controls access to an object. Each object has an associated monitor that a thread can lock or unlock. When a thread enters a synchronized method or block, it acquires the monitor lock, and other threads trying to enter synchronized code on the same object are blocked until the lock is released.

**Levels of Synchronization:**
1. **Object Level:** Synchronize instance methods or blocks using the object's monitor.
2. **Class Level:** Synchronize static methods or blocks using the class's monitor.

**Easy to Remember:** Use object's monitor for instance methods/blocks; use class's monitor for static methods/blocks.

### 27. Ensuring N Threads Can Access N Resources Without Deadlock
**Answer:** To avoid deadlocks, follow these principles:
1. **Resource Ordering:** Assign a consistent order to acquire resources.
2. **Avoid Nested Locks:** Prevent threads from holding multiple locks simultaneously.
3. **Use Timeout:** Implement timeouts when attempting to acquire a lock.
4. **Deadlock Detection:** Use algorithms to detect and recover from deadlocks.

**Easy to Remember:** Order resources, avoid nested locks, use timeouts, and detect deadlocks.

### 28. What is a monitor lock?
**Anser:** A monitor lock, often referred to as a mutex (mutual exclusion), is a [synchronization mechanism](#26-thread-synchronization-inside-a-monitor) used in concurrent programming to control access to a shared resource by multiple threads. It ensures that only one thread can access the resource at a time, preventing race conditions and ensuring thread safety.

**Easy to Remember:** Ensures only one thread accesses a resource at a time

### 29. Difference Between the Runnable and Callable Interfaces

**Runnable:**
- **Definition:** The `Runnable` interface represents a task that can be executed by a thread. It has a single `run` method that does not return any value or throw any checked exception.
- **Usage:**
  ```java
  public class MyRunnable implements Runnable {
      @Override
      public void run() {
          System.out.println("Runnable is running");
      }
  }

  public static void main(String[] args) {
      Thread thread = new Thread(new MyRunnable());
      thread.start();
  }
  ```

**Callable:**
- **Definition:** The `Callable` interface is similar to `Runnable` but can return a result and throw a checked exception. It has a single `call` method.
- **Usage:**
  ```java
  public class MyCallable implements Callable<String> {
      @Override
      public String call() throws Exception {
          return "Callable result";
      }
  }

  public static void main(String[] args) throws Exception {
      ExecutorService executor = Executors.newFixedThreadPool(1);
      Future<String> future = executor.submit(new MyCallable());
      System.out.println(future.get());
      executor.shutdown();
  }
  ```

**Easy to Remember:**
- **Runnable:** `run()` method, no return value, no checked exception.
- **Callable:** `call()` method, returns a value, can throw a checked exception.

### 30. What is Race Conditions?

**Definition:**
- **Race Condition:** A race condition occurs in a multithreaded environment when two or more threads access shared data and try to change it at the same time. The final outcome depends on the sequence of thread execution, which is unpredictable and can lead to incorrect behavior or program errors.

**Usage Example:**
- **Scenario:** Imagine two threads trying to increment a shared counter variable.
  ```java
  public class Counter {
      private int count = 0;

      public void increment() {
          count++;
      }

      public int getCount() {
          return count;
      }
  }

  public static void main(String[] args) {
      Counter counter = new Counter();
      Runnable task = () -> {
          for (int i = 0; i < 1000; i++) {
              counter.increment();
          }
      };

      Thread thread1 = new Thread(task);
      Thread thread2 = new Thread(task);

      thread1.start();
      thread2.start();

      try {
          thread1.join();
          thread2.join();
      } catch (InterruptedException e) {
          e.printStackTrace();
      }

      System.out.println("Final count: " + counter.getCount());
  }
  ```

**Problem:**
- **Race Condition:** The expected final count should be 2000, but due to race conditions, it may be less because the increment operations are not atomic.

**Solution:**
- **Synchronization:** To prevent race conditions, use synchronization to ensure that only one thread can access the critical section of code at a time.
  ```java
  public class Counter {
      private int count = 0;

      public synchronized void increment() {
          count++;
      }

      public int getCount() {
          return count;
      }
  }
  ```

**Easy to Remember:**
- **Race Condition:** Happens when multiple threads modify shared data simultaneously, leading to unpredictable results. Use synchronization to prevent it.


## Advanced Threads

### 31. What Is a Daemon Thread, What Are Its Use Cases? How Can You Create a Daemon Thread?
A daemon thread is a thread that does not prevent the JVM from exiting. When all non-daemon threads are terminated, the JVM simply abandons all remaining daemon threads. Daemon threads are typically used for supportive or service tasks for other threads, but you should note that they may be abandoned at any time.

To start a thread as a daemon, use the `setDaemon(true)` method before calling `start()`:

```java
Thread daemon = new Thread(() -> System.out.println("Hello from daemon!"));
daemon.setDaemon(true);
daemon.start();
```

If you run this as a part of the `main()` method, the message might not get printed if the main thread terminates before the daemon thread gets to the point of printing the message. It is generally recommended to avoid doing any I/O in daemon threads, as they may not be able to execute their finally blocks and close resources if abandoned.

### 32. What Is the Thread’s Interrupt Flag? How Can You Set and Check It? How Does It Relate to the InterruptedException?
The interrupt flag, or interrupt status, is an internal thread flag that is set when the thread is interrupted. To set it, call `thread.interrupt()` on the thread object.

If a thread is currently inside one of the methods that throw `InterruptedException` (e.g., `wait`, `join`, `sleep`), then this method immediately throws `InterruptedException`. The thread can handle this exception according to its own logic.

If a thread is not inside such a method and `thread.interrupt()` is called, nothing special happens. It is the thread’s responsibility to periodically check the interrupt status using the static `Thread.interrupted()` or instance `isInterrupted()` method. The difference between these methods is that the static `Thread.interrupted()` clears the interrupt flag, while `isInterrupted()` does not.

### 33. What Are Executor and ExecutorService? What Are the Differences Between These Interfaces?
`Executor` and `ExecutorService` are two related interfaces in the `java.util.concurrent` framework. `Executor` is a simple interface with a single `execute` method that accepts `Runnable` instances for execution. In most cases, this is the interface that your task-executing code should depend on.

`ExecutorService` extends the `Executor` interface with multiple methods for handling and checking the lifecycle of a concurrent task execution service (e.g., termination of tasks in case of shutdown) and methods for more complex asynchronous task handling, including `Future`s.

### 34. What Are the Available Implementations of ExecutorService in the Standard Library?
The `ExecutorService` interface has three standard implementations:

- **ThreadPoolExecutor**: Executes tasks using a pool of threads. Once a thread finishes executing the task, it goes back into the pool. If all threads in the pool are busy, the task has to wait for its turn.
- **ScheduledThreadPoolExecutor**: Schedules task execution instead of running it immediately when a thread is available. It can also schedule tasks with a fixed rate or fixed delay.
- **ForkJoinPool**: A special `ExecutorService` for dealing with recursive algorithm tasks. It implements the work-stealing algorithm, which allows it to use available threads more efficiently.

### 35. What Is the Java Memory Model (JMM)? Describe Its Purpose and Basic Ideas.
The Java Memory Model (JMM) is a part of the Java language specification described in Chapter 17.4. It specifies how multiple threads access common memory in a concurrent Java application and how data changes by one thread are made visible to other threads. The JMM guarantees help ensure that multithreaded code is stable and portable across various architectures.

The main notions of JMM are:
- **Actions**: Inter-thread actions that can be executed by one thread and detected by another thread, such as reading or writing variables, locking/unlocking monitors, etc.
- **Synchronization Actions**: A subset of actions, such as reading/writing a volatile variable or locking/unlocking a monitor.
- **Program Order (PO)**: The observable total order of actions inside a single thread.
- **Synchronization Order (SO)**: The total order between all synchronization actions, which must be consistent with Program Order.
- **synchronizes-with (SW)**: A relation between certain synchronization actions, such as unlocking a monitor and locking the same monitor.
- **Happens-before Order**: Combines PO with SW to create a partial ordering of all actions between threads. If one action happens-before another, then the results of the first action are observable by the second action.
- **Happens-before Consistency**: A set of actions is HB-consistent if every read observes either the last write to that location in the happens-before order or some other write via a data race.

If a program is correctly synchronized, all its executions appear to be sequentially consistent, meaning you can reason about the multithreaded program as a set of actions occurring in some sequential order.

### 36. What Is a Volatile Field and What Guarantees Does the JMM Hold for Such Field?
A volatile field has special properties according to the Java Memory Model. The reads and writes of a volatile variable are synchronization actions, meaning that they have a total ordering. A read of a volatile variable is guaranteed to observe the last write to this variable.

If a field is accessed from multiple threads, with at least one thread writing to it, it should be made volatile to ensure that there is a consistent and atomic view of the variable across all threads.

### 37. Which of the Following Operations Are Atomic?
- Writing to a non-volatile int: **Yes**
- Writing to a volatile int: **Yes**
- Writing to a non-volatile long: **No**
- Writing to a volatile long: **Yes**
- Incrementing a volatile long: **No**

A write to an int (32-bit) variable is guaranteed to be atomic, whether it is volatile or not. A long (64-bit) variable could be written in two separate steps, so without the volatile modifier, there is no atomicity guarantee. However, a volatile long variable is guaranteed to be accessed atomically. The increment operation is not atomic and requires additional synchronization, such as using `AtomicInteger` or `AtomicLong`.

### 38. What Special Guarantees Does the JMM Hold for Final Fields of a Class?
The JVM guarantees that final fields of a class will be initialized before any thread gets hold of the object. This ensures that a reference to an object is not published before all its fields are fully initialized. When creating an immutable object, all its fields should be declared final to ensure proper initialization and visibility across threads.


### 39. If Two Threads Call a Synchronized Method on Different Object Instances Simultaneously, Could One of These Threads Block? What If the Method Is Static?
- **Instance Method**: If the method is an instance method, the instance acts as a monitor for the method. Two threads calling the method on different instances acquire different monitors, so none of them gets blocked.
- **Static Method**: If the method is static, the monitor is the `Class` object. For both threads, the monitor is the same, so one of them will probably block and wait for the other to exit the synchronized method.

### 40. Describe the Conditions of Deadlock, Livelock, and Starvation. Describe the Possible Causes of These Conditions.
- **Deadlock**: A condition where a group of threads cannot make progress because each thread is waiting to acquire a resource held by another thread in the group. A common case is when two threads need to lock both of two resources to progress, but each thread holds one resource and waits for the other.
- **Livelock**: A situation where multiple threads keep responding to each other’s actions or events but cannot make progress. Threads are alive and not blocked, but they keep overwhelming each other with useless work.
- **Starvation**: A condition where a thread is unable to acquire a resource because other threads occupy it for too long or have higher priority. As a result, the thread cannot make progress and complete its tasks.

### 41. Describe the Purpose and Use-Cases of the Fork/Join Framework.
The fork/join framework allows parallelizing recursive algorithms. The main problem with parallelizing recursion using something like `ThreadPoolExecutor` is that it may quickly run out of threads, as each recursive step would require its own thread. The `ForkJoinPool` class, an implementation of `ExecutorService`, uses the work-stealing algorithm, where idle threads try to “steal” work from busy threads. This allows spreading calculations between different threads and making progress while using fewer threads than a regular thread pool.

### 42. What is CompletableFuture?

A `CompletableFuture` is a class in Java that represents a future result of an asynchronous computation. It allows you to write non-blocking code, where tasks can run concurrently and notify you when they are done, without waiting for them to finish.

Here's a simple explanation:

- **Future**: A placeholder for a result that will be available in the future.
- **CompletableFuture**: An enhanced version of Future that allows you to explicitly complete it, chain multiple asynchronous tasks, and handle them more flexibly.

### Key Points to Remember:

1. **Asynchronous Computation**: `CompletableFuture` allows you to run tasks asynchronously, so your program can continue doing other things while waiting for the result.
2. **Chaining**: You can chain multiple `CompletableFuture` tasks together using methods like `thenApply`, `thenAccept`, `thenRun`, etc., to process the result of one task in the next.
3. **Non-Blocking**: Unlike traditional `Future`, which blocks the thread until the result is available, `CompletableFuture` provides non-blocking methods to get the result, like `whenComplete`, `thenCompose`, etc.
4. **Completion**: You can manually complete a `CompletableFuture` using the `complete` method if needed.

### Example:

Here's a simple example to illustrate how `CompletableFuture` works:

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureExample {
    public static void main(String[] args) {
        CompletableFuture.supplyAsync(() -> "Hello")
                .thenApply(greeting -> greeting + " World")
                .thenAccept(result -> System.out.println(result));
        
        // Output: Hello World
    }
}
```

In this example:
- `supplyAsync` runs the task that returns "Hello" asynchronously.
- `thenApply` processes the result by appending " World".
- `thenAccept` consumes the final result and prints it out.

Remember, `CompletableFuture` is powerful for managing complex asynchronous workflows in a simple, readable manner.


### **Multithreading and Asynchronous Programming in Java**

#### **1. Multithreading**
- **Definition**: Using multiple threads within a process to run tasks concurrently.
- **Key Tool**: `ExecutorService` for managing thread pools.
- **Blocking Nature**: Threads are often blocked while waiting for resources.
- **Use Case**: CPU-bound tasks, parallel computations.

**Example: Using `ExecutorService` with Output**
```java
ExecutorService executor = Executors.newFixedThreadPool(3);
Future<String> future1 = executor.submit(() -> "Result from Task 1");
System.out.println(future1.get()); // Blocking call to get result
executor.shutdown();
```

**Batch Execution with `invokeAll`**
```java
List<Callable<String>> tasks = Arrays.asList(
    () -> "Result 1", 
    () -> "Result 2", 
    () -> "Result 3"
);
List<Future<String>> futures = executor.invokeAll(tasks);
for (Future<String> future : futures) System.out.println(future.get());
executor.shutdown();
```

---

#### **2. Asynchronous Programming**
- **Definition**: Non-blocking execution where tasks notify upon completion.
- **Key Tool**: `CompletableFuture` for chaining tasks and handling results.
- **Non-Blocking Nature**: Tasks do not block the thread; callbacks handle results.
- **Use Case**: I/O-bound tasks, such as API calls or database queries.

**Example: Using `CompletableFuture`**
```java
CompletableFuture.supplyAsync(() -> "Task 1 result")
                 .thenApply(result -> result + " processed!")
                 .thenAccept(System.out::println); // Non-blocking
```

**Handling Multiple Async Tasks**
```java
List<CompletableFuture<String>> futures = IntStream.range(1, 4)
    .mapToObj(i -> CompletableFuture.supplyAsync(() -> "Result from Task " + i))
    .collect(Collectors.toList());
CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]))
                 .thenRun(() -> futures.forEach(f -> System.out.println(f.join())));
```

---

#### **3. Combining Multithreading and Asynchronous Programming**
- **Hybrid Approach**: Use `ExecutorService` for thread pools and `CompletableFuture` for task chaining and non-blocking behavior.
- **Use Case**: Efficient handling of both CPU- and I/O-bound tasks.

**Example: Combining `ExecutorService` and `CompletableFuture`**
```java
ExecutorService executor = Executors.newFixedThreadPool(3);
CompletableFuture.supplyAsync(() -> "Task 1", executor)
                 .thenAccept(result -> System.out.println(result + " completed!"));
executor.shutdown();
```

---

#### **Comparison**
| **Aspect**             | **Multithreading**                      | **Asynchronous Programming**          |
|------------------------|-----------------------------------------|---------------------------------------|
| **Definition**         | Multiple threads for concurrent tasks. | Non-blocking execution with callbacks.|
| **Blocking**           | Blocking (e.g., `Future.get()`).        | Non-blocking (`thenApply`, `thenAccept`). |
| **Use Case**           | CPU-bound tasks, parallel computations. | I/O-bound tasks, API calls.           |
| **Tools**              | `ExecutorService`, `Future`.            | `CompletableFuture`.                  |
| **Thread Management**  | Manual management.                      | Uses `ForkJoinPool` or custom executor.|

---

### **Best Practices**
1. Use **ExecutorService** for low-level thread management.
2. Use **CompletableFuture** for chaining and non-blocking workflows.
3. Combine both for efficient handling of mixed workloads.
4. For highly scalable systems, consider **Reactive Programming** with `Flux` (Project Reactor).

This concise summary provides key examples and concepts for your study reference. Let me know if you'd like more details!