#### 1. Need for Threads in Java
**Answer:** Threads allow multiple tasks to run concurrently within a single program, improving performance and responsiveness.

**Easy to Remember:** Threads enable concurrent task execution.

#### 2. Creating a Thread
**Answer:** You can create a thread by extending the `Thread` class or implementing the `Runnable` interface.

**Easy to Remember:** Two ways - extend `Thread` or implement `Runnable`.

#### 3. Creating a Thread by Extending Thread Class
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

#### 4. Creating a Thread by Implementing Runnable Interface
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

#### 5. Running a Thread in Java
**Answer:** Start the thread by calling its `start()` method.

**Easy to Remember:** Call `start()` to run the thread.

#### 6. Different States of a Thread (Thread States (High-Level))
**Answer:** 
1. **New:** Thread is created but not started.
2. **Runnable:** Thread is ready to run.
3. **Blocked:** Thread is blocked and waiting for a monitor lock.
4. **Waiting:** Thread is waiting indefinitely for another thread.
5. **Timed Waiting:** Thread is waiting for a specified period.
6. **Terminated:** Thread has finished execution.

**Easy to Remember:** New, Runnable, Blocked, Waiting, Timed Waiting, Terminated.

#### 7. Thread Priority and Changing Priority
**Answer:** Priority determines the relative importance of a thread.
```java
thread.setPriority(Thread.MAX_PRIORITY); // Sets priority to 10
```

**Easy to Remember:** Use `setPriority()` to change thread priority.

#### 8. ExecutorService
**Answer:** `ExecutorService` is a framework for managing a pool of threads.

**Easy to Remember:** Manages thread pools for concurrent execution.

#### 9. Example of ExecutorService
**Answer:** 
```java
ExecutorService executor = Executors.newFixedThreadPool(5);
executor.submit(() -> System.out.println("Task executed"));
executor.shutdown();
```

**Easy to Remember:** Create pool with `Executors`, submit tasks, shutdown.

#### 10. Creating Executor Services
**Answer:** 
1. **FixedThreadPool:** A fixed-size thread pool.
2. **CachedThreadPool:** Creates new threads as needed.
3. **SingleThreadExecutor:** A single worker thread.

**Easy to Remember:** Fixed, Cached, Single-thread executor services.

#### 11. Checking ExecutionService Task Execution Success
**Answer:** Use `Future.get()` method.
```java
Future<String> future = executor.submit(callable);
String result = future.get(); // Checks if the task completed successfully
```

**Easy to Remember:** Use `Future.get()` to check task completion.

#### 12. Callable and Executing from ExecutorService
**Answer:** 
```java
Callable<String> callable = () -> "Task result";
Future<String> future = executor.submit(callable);
String result = future.get();
```

**Easy to Remember:** Callable returns a result, use `submit(callable)`.

#### 13. Synchronization of Threads
**Answer:** Ensures that only one thread accesses a resource at a time.

**Easy to Remember:** Ensures one thread access to resources.

#### 14. Example of a Synchronized Block
**Answer:** 
```java
synchronized(this) {
    // synchronized code
}
```

**Easy to Remember:** Use `synchronized(this)` to create a synchronized block.

#### 15. Synchronizing a Static Method
**Answer:** Yes, use the `synchronized` keyword.
```java
synchronized static void syncMethod() {
    // synchronized code
}
```

**Easy to Remember:** Use `synchronized` keyword on static method.

#### 16. Use of Join Method in Threads
**Answer:** Waits for a thread to finish its execution.
```java
thread.join();
```

**Easy to Remember:** Use `join()` to wait for thread completion.

#### 17. Other Important Methods in Threads
**Answer:**
1. **sleep(long millis):** Pauses the thread.
2. **yield():** Temporarily pauses the thread to allow others to execute.
3. **interrupt():** Interrupts a thread.

**Easy to Remember:** sleep, yield, interrupt.

#### 18. Deadlock
**Answer:** A situation where two or more threads are blocked forever, waiting for each other.

**Easy to Remember:** Threads block each other permanently.

#### 19. Important Methods for Inter-Thread Communication
**Answer:** `wait()`, `notify()`, `notifyAll()`.

**Easy to Remember:** Key methods: wait, notify, notifyAll.

#### 20. Use of Wait Method
**Answer:** Causes the current thread to wait until another thread invokes `notify()` or `notifyAll()`.

**Easy to Remember:** Waits for notify/notifyAll.

#### 21. Use of Notify Method
**Answer:** Wakes up a single thread waiting on the object's monitor.

**Easy to Remember:** Wakes one waiting thread.

#### 22. Use of NotifyAll Method
**Answer:** Wakes up all threads waiting on the object's monitor.

**Easy to Remember:** Wakes all waiting threads.

#### 23. Synchronized Program with Wait and Notify Methods
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

#### 24. Difference Between Processes and Threads
**Answer:**
- **Processes:** Independent execution units with their own memory space. Communication between processes is more complex.
- **Threads:** Smaller units within a process that share the same memory space. Easier communication and lower overhead.

**Easy to Remember:** Processes are independent with separate memory; threads are part of a process sharing memory.


#### 25. Difference Between Synchronized Method and Synchronized Block
**Answer:**
- **Synchronized Method:** Locks the entire method, affecting all the code within it.
- **Synchronized Block:** Locks only the specific block of code, allowing more fine-grained control over synchronization.

**Easy to Remember:** Method locks the entire method; block locks specific code segment.

#### 26. Thread Synchronization Inside a Monitor
**Answer:** Thread synchronization in Java occurs within a monitor, which is a mechanism that controls access to an object. Each object has an associated monitor that a thread can lock or unlock. When a thread enters a synchronized method or block, it acquires the monitor lock, and other threads trying to enter synchronized code on the same object are blocked until the lock is released.

**Levels of Synchronization:**
1. **Object Level:** Synchronize instance methods or blocks using the object's monitor.
2. **Class Level:** Synchronize static methods or blocks using the class's monitor.

**Easy to Remember:** Use object's monitor for instance methods/blocks; use class's monitor for static methods/blocks.

#### 27. Ensuring N Threads Can Access N Resources Without Deadlock
**Answer:** To avoid deadlocks, follow these principles:
1. **Resource Ordering:** Assign a consistent order to acquire resources.
2. **Avoid Nested Locks:** Prevent threads from holding multiple locks simultaneously.
3. **Use Timeout:** Implement timeouts when attempting to acquire a lock.
4. **Deadlock Detection:** Use algorithms to detect and recover from deadlocks.

**Easy to Remember:** Order resources, avoid nested locks, use timeouts, and detect deadlocks.

