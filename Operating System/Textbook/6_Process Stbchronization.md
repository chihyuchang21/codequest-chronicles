# Chapter 6: Synchronization Tools

## 6.1 Background
- **Concurrent and Parallel Execution**:
  - Processes execute concurrently (single-core) or in parallel (multi-core).
  - Issues arise when processes access shared data simultaneously.
- **Producer-Consumer Example**:
  - Introduces the need for proper synchronization to manage shared data.

---

## 6.2 The Critical-Section Problem
- **Definition**: A code section where shared data may be manipulated, potentially leading to race conditions.
- **Requirements for a Solution**:
  1. **Mutual Exclusion**: Only one process can be in its critical section at a time.
  2. **Progress**: Processes must decide which will enter the critical section in a finite time.
  3. **Bounded Waiting**: Limits the time a process waits to enter its critical section.

---

## 6.3 Peterson’s Solution
- **Software-based Mutual Exclusion**:
  - A classic algorithm ensuring mutual exclusion for two processes.
  - Relies on two variables (`flag` and `turn`).

---

## 6.4 Hardware Support for Synchronization
- **Memory Barriers**:
  - Ensures instruction ordering for consistency across processors.
- **Hardware Instructions**:
  - **Test-and-Set** and **Compare-and-Swap (CAS)**:
    - Atomic operations to modify shared data without interference.

---

## 6.5 Mutex Locks
- **Definition**:
  - A software-based locking mechanism for mutual exclusion.
- **Usage**:
  - `acquire()` locks the resource.
  - `release()` unlocks it.
- **Limitations**:
  - Busy waiting may occur.

---

## 6.6 Semaphores
- **Definition**:
  - A more versatile synchronization tool using counters.
- **Operations**:
  - `wait()` decrements the semaphore; blocks if value < 0.
  - `signal()` increments the semaphore; unblocks waiting processes.
- **Types**:
  1. **Binary Semaphore**: Acts like a mutex.
  2. **Counting Semaphore**: Tracks multiple resource availability.

---

## 6.7 Monitors
- **High-Level Synchronization**:
  - Encapsulates shared data and methods.
  - Ensures only one process is active inside the monitor.
- **Condition Variables**:
  - Used for custom synchronization schemes.
  - Operations:
    - `wait()` suspends the process.
    - `signal()` resumes a waiting process.

---

## 6.8 Liveness
- **Issues**:
  1. **Deadlock**: Processes waiting indefinitely for each other.
  2. **Starvation**: A process never gets access to resources.

---

## 6.9 Evaluation
- **Comparison of Tools**:
  - Mutex locks are simple but unsuitable for high contention.
  - CAS-based approaches work well under low to moderate contention.
  - Monitors and condition variables are user-friendly but may have overhead.

---

## 6.10 Summary
- **Key Points**:
  - Race conditions and critical-section problems require synchronization.
  - Tools like mutex locks, semaphores, and monitors address these issues.
  - Proper choice of tools depends on contention levels and application needs.

---

### Figures
- *See Figure 6.11*: Pseudocode of Monitor Syntax.
- *See Figure 6.13*: Monitor with Condition Variables.
