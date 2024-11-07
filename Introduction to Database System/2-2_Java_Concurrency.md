# 1. Starting Threads in Java
- **Creating Threads**:
    - Implement the `Runnable` interface and override the `run()` method.
      ```java
      public class HelloRunnable implements Runnable {
          @Override
          public void run() {
              System.out.println("Hello from a thread!");
          }
          
          public static void main(String[] args) {
              (new Thread(new HelloRunnable())).start();
          }
      }
      ```
    - Extend the `Thread` class and override the `run()` method.
      ```java
      public class HelloThread extends Thread {
          @Override
          public void run() {
              System.out.println("Hello from a thread!");
          }
          
          public static void main(String[] args) {
              (new HelloThread()).start();
          }
      }
      ```
- **What Happens When Starting a Thread**:
    - Each thread has its own stack but shares the heap with other threads.
    - The CPU handles both `main` and `run()` in parallel, executing both concurrently.

# 2. Memory Model in Multithreading
- **Thread Memory Layout**:
    - **Heap**: Shared memory area where objects reside; accessible by all threads.
    - **Stack**: Each thread has its own stack for managing its local variables and method calls.
- **Shared Object Access**:
    - Two threads can access the same object by passing it to their constructors.
      ```java
      public static void main(String[] args) {
          Counter counter = new Counter();
          (new Thread(new HelloRunnableA(counter))).start();
          (new Thread(new HelloRunnableB(counter))).start();
      }
      ```
    - This shared access can lead to race conditions if threads simultaneously modify the object.

# 3. Synchronization and Race Conditions
- **Problem with Concurrent Access**:
    - Without synchronization, two threads may read and write to the same variable unpredictably, causing lost updates.
    - Example issue with `Counter`:
      ```java
      class Counter {
          private int c = 0;
          
          public void set(int c) { this.c = c; }
          public int get() { return c; }
      }
      ```
    - Scenario:
        1. Thread A reads `c`.
        2. Thread B reads `c`.
        3. Both increment `c`.
        4. Each sets `c` back, potentially overwriting each other's result.
- **Using `synchronized` to Prevent Issues**:
    - Only one thread can access a synchronized block at a time.
    - Synchronizing a method:
      ```java
      public synchronized int get() { return c; }
      public synchronized void set(int c) { this.c = c; }
      ```

# 4. Correct Synchronization and Thread Communication
- **Ensuring Atomic Operations**:
    - Use synchronized blocks to ensure operations like increment and decrement are atomic.
    - Example:
      ```java
      synchronized(counter) {
          int c = counter.get();
          c++;
          counter.set(c);
      }
      ```
- **Blocking and Waiting**:
    - **`wait()` and `notifyAll()`**:
        - A thread in a synchronized block can call `wait()` to release the lock and enter a waiting state, allowing other threads to proceed.
        - Another thread can use `notifyAll()` to wake up waiting threads.
        - Example in a queue:
          ```java
          synchronized(queue) {
              while(queue.size() == 10) {
                  queue.wait();
              }
              queue.add(item);
              queue.notifyAll();
          }
          ```
    - **Best Practice**: Wrap `wait()` in a loop to prevent spurious wake-ups.





