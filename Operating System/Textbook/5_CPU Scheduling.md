# 5. CPU Scheduling
## 5.1 Basic Concepts
- **CPU Scheduling**: Focuses on managing multiple processes where more than one process is ready to execute. The CPU scheduler selects from among the processes that are ready to execute and allocates the CPU to one of them.
- **Importance**: Efficient CPU scheduling is central to good system performance.

## 5.2 Scheduling Criteria
- **CPU Utilization**: Keeping the CPU as busy as possible is a primary goal.
- **Throughput**: Number of processes completed per time unit; higher is better.
- **Turnaround Time**: Time taken for a process to complete after submission. Reducing turnaround time is crucial for batch systems.
- **Waiting Time**: Total time a process has been in the ready queue; minimizing waiting time is crucial for interactive performance.
- **Response Time**: Time from request submission until the first response is produced. Important in environments where quick reactions are needed from the system.

## 5.3 Scheduling Algorithms
- **First-Come, First-Served (FCFS)**: Simplest scheduling algorithm that operates on a first-in, first-out basis.
- **Shortest-Job-First (SJF)**: Associates each process with the length of its next CPU burst and schedules the process with the shortest time.
- **Priority Scheduling**: Processes are assigned a priority, and the CPU is allocated to the process with the highest priority.
- **Round Robin (RR)**: Each process gets a small unit of CPU time (time quantum), usually 10-100 milliseconds. After this time has elapsed, the process is preempted and added to the end of the ready queue.
- **Multilevel Queue Scheduling**: Partitions the ready queue into several separate queues; processes are permanently assigned to one queue, generally based on some property of the process, such as memory size, process priority, or process type.

## 5.4 Thread Scheduling
- **Overview**: Modern operating systems may schedule user-level threads or kernel-level threads.
- **Models**: Many-to-one model, one-to-one model, and many-to-many model.

## 5.5 Multi-Processor Scheduling
- **Context**: Involves scheduling processes on a system with multiple processors.
- **Challenges**: Load balancing and affinity, particularly keeping in mind the need to balance the workload across cores.

## 5.6 Real-Time CPU Scheduling
- **Soft Real-Time Systems**: These systems have more lenient timing constraints.
- **Hard Real-Time Systems**: These systems have strict timing constraints; missed deadline can lead to serious consequences.

## 5.7 Operating-System Examples
- **Linux Scheduling**: Uses a complex scheduling algorithm that includes time-sharing and real-time policies.
- **Windows Scheduling**: Uses a preemptive priority-based scheduling mechanism.

## 5.8 Algorithm Evaluation
- **Methods**: Deterministic modeling, queuing models, simulations, and empirical measurements are used to evaluate the efficacy of scheduling algorithms.

## 5.9 Summary
- **Key Takeaways**: Effective scheduling is crucial for maximizing system utilization and user satisfaction. Different systems and applications may require different scheduling algorithms for optimal performance.
