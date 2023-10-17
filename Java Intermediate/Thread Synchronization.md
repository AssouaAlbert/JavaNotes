# Thread Synchronization

Thread synchronization in Java is the process of controlling access to shared resources or critical sections of code to ensure that only one thread can execute that code at a time. Synchronization is crucial when multiple threads access shared data concurrently to prevent race conditions and data inconsistencies. Java provides several mechanisms for thread synchronization, including the use of the `synchronized` keyword, locks, and other synchronization constructs. Here are the key concepts and techniques for thread synchronization in Java:

1. **`synchronized` Keyword:**
   - The `synchronized` keyword can be applied to methods or code blocks to ensure that only one thread can execute the synchronized code at a time.
   - When a thread enters a synchronized method or block, it acquires a lock on the object, and other threads trying to access the synchronized code must wait until the lock is released.
   
   Example of synchronizing a method:
   ```java
   public synchronized void synchronizedMethod() {
       // Synchronized code
   }
   ```

   Example of synchronizing a code block:
   ```java
   synchronized (lockObject) {
       // Synchronized code
   }
   ```

2. **`wait()` and `notify()`:**
   - The `wait()` and `notify()` methods are used for inter-thread communication and coordination.
   - Threads can use `wait()` to release the lock on an object and wait until another thread calls `notify()` or `notifyAll()` to wake them up.
   - `notify()` and `notifyAll()` are used to wake up waiting threads.

   Example of using `wait()` and `notify()`:
   ```java
   synchronized (sharedObject) {
       // Critical section
       sharedObject.wait(); // Current thread releases the lock and waits
   }
   ```

   In another thread:
   ```java
   synchronized (sharedObject) {
       // Perform some work
       sharedObject.notify(); // Notify waiting threads
   }
   ```

3. **Locks (ReentrantLock):**
   - Java provides the `java.util.concurrent.locks.ReentrantLock` class, which offers more flexibility and control than the `synchronized` keyword.
   - You can explicitly acquire and release locks, implement conditions, and handle interruptions.

   Example using `ReentrantLock`:
   ```java
   ReentrantLock lock = new ReentrantLock();
   lock.lock(); // Acquire the lock
   try {
       // Critical section
   } finally {
       lock.unlock(); // Release the lock
   }
   ```

4. **Synchronized Collections:**
   - Java offers synchronized collections such as `Collections.synchronizedList()`, `Collections.synchronizedMap()`, etc., which provide synchronized access to data structures.
   
   Example using a synchronized list:
   ```java
   List<String> synchronizedList = Collections.synchronizedList(new ArrayList<>());
   ```

5. **Volatile Keyword:**
   - The `volatile` keyword is used to declare variables to ensure that changes made by one thread are visible to other threads.
   - It is typically used for simple flags or variables that do not require complex synchronization.

   Example of a volatile variable:
   ```java
   private volatile boolean flag = false;
   ```

6. **Atomic Classes:**
   - The `java.util.concurrent.atomic` package provides atomic classes like `AtomicInteger`, `AtomicLong`, and `AtomicReference`, which offer atomic operations without the need for explicit synchronization.

   Example using `AtomicInteger`:
   ```java
   AtomicInteger atomicInt = new AtomicInteger(0);
   atomicInt.incrementAndGet(); // Atomic increment
   ```

Proper thread synchronization is essential to avoid race conditions and maintain data integrity when multiple threads access shared resources. The choice of synchronization mechanism depends on the specific requirements of your multithreading scenario, and using the wrong mechanism can lead to issues like deadlock or performance problems.

## NoteSynchronization is the capability to control the access of multiple threads to any shared resource.
- In a multithreaded environment, a race condition occurs when 2 or more threads attempt to access the same resource.
- Using the synchronized keyword on a piece of logic enforces that only one thread can access the resource at any given time.
- synchronized blocks or methods can be created using the keyword.
- Also, one way a class can be "thread-safe" is if all of its methods are synchronized.