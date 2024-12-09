# 4. Threads
## **4.1 Overview**
- **Threads**: A thread is a basic unit of CPU utilization; it comprises a thread ID, a program counter, a register set, and a stack.
    <img src="pic/4-1-1.png" alt="view" width="500">
    <img src="pic/4-1-2.png" alt="view" width="500">

## **4.2 Multicore Programming**
- **Importance**: Addresses the utilization of multiple CPU cores for improving performance.
- **Challenges**: Discusses the complexities involved in concurrent execution and resource sharing across cores.

## **4.3 Multithreading Models**
- **Models Covered**: Reviews different models of system-level and user-level multithreading.
    - *Many-to-One Model*
        - Many user threads correspond to a single kernel thread.
        - Think of user threads as units competing for the CPU.
        - There's only one CPU, so parallel processing is not possible (since there's just one!).
        - Actually… it won’t be faster.
    
        <img src="pic/4-3-1.png" alt="view" width="300">    
    
    - *One-to-One Model*
        - One user thread corresponds to one kernel thread.
        - When one thread is blocked (e.g., making a blocking system call), others will continue processing.
        - Higher management cost: Creating a user thread necessitates the creation of a corresponding kernel thread.

        <img src="pic/4-3-2.png" alt="view" width="300">    

    - *Many-to-Many Model*
        - Automatically establishes a mapping between user threads and kernel threads.
        - Lower management cost.

        <img src="pic/4-3-3.png" alt="view" width="300">    


## **4.4 Thread Libraries**
- **Purpose**: Provides the programmer with an API for creating and managing threads.
- **Examples**: POSIX threads, Java threading mechanisms.

## **4.5 Implicit Threading**
- **Techniques**: Discusses the abstraction of thread management from the programmer to simplify concurrent programming.
- **Tools**: Describes language-level features and compiler strategies that help in implicit threading.

## **4.6 Threading Issues**
- **Concerns**: Identifies common issues like synchronization, data splitting, and resource allocation.
- **Solutions**: Provides best practices for avoiding or resolving these issues.

## **4.7 Operating-System Examples**
- **Case Studies**: Demonstrates how modern operating systems implement threading and handle concurrency.
- **Systems Discussed**: Examples from Linux, Windows, and macOS.