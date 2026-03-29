# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:**
A process is a program in execution that has its own isolated memory space and system resources, making it relatively heavy to create and manage. A thread, often called a lightweight process, is a unit of execution within a process that shares the same memory and resources as other threads in that process. We used threads in this simulation because they are much faster to create and switch between (lower context-switching overhead) compared to actual OS-level processes. This allows us to efficiently simulate multiple concurrent entities running in our scheduler without the heavy resource burden of creating distinct JVM processes for each simulated process.

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:**
In Round-Robin scheduling, if a process does not complete its execution within the assigned time quantum, it is preempted by the scheduler. A context switch occurs, and the process is placed back at the tail (end) of the ready queue to wait for its next turn. It will not run again until all other processes ahead of it in the queue have been given their respective time slices.

Example from my output:
```text
[Time 15] Process P1 (Priority: 5) execution started. Remaining time: 8
[Time 20] Process P1 time quantum expired. Context switch. Remaining time: 3
[Time 20] Process P1 added to end of ready queue.
```

**Explanation of example:**
In this snippet, Process P1 starts running with 8 units of time remaining. The time quantum is 5 units. Since P1 needs more time than the quantum, it gets preempted at Time 20, a context switch happens, and it is moved back to the ready queue with 3 units of execution time still left.

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**
1. **New**: P1 is in the New state when its `Process` (or `Thread`) object is instantiated in memory, but the `start()` method has not yet been called.
2. **Runnable**: P1 enters the Runnable state when `start()` is invoked and it is placed into the scheduler's ready queue, waiting for its turn on the CPU.
3. **Running**: P1 is in the Running state when the CPU scheduler dequeues it from the ready queue and allocates CPU time to it for the duration of its time quantum.
4. **Waiting**: P1 would enter a Waiting state if it requested an I/O operation, or intrinsically when it is preempted by the timer and sits in the ready queue waiting for the CPU again.
5. **Terminated**: P1 enters the Terminated state when it has finished its total execution time (remaining burst time becomes zero) and its `run()` method completes.

---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: Web Server Request Handling

**Description**: 
A web server (such as Apache or Nginx) handling multiple incoming HTTP requests from different clients simultaneously.

**Why Round-Robin works well here**: 
Round-Robin ensures that all client connections receive a fair share of CPU processing time. This prevents a single computationally expensive request from blocking the server and causing timeouts for other users, thereby ensuring quick and responsive handling of many smaller requests.

### Example 2: Interactive Desktop Environments

**Description**: 
An operating system managing various user-space applications (like a web browser, word processor, and music player) in a graphical user interface.

**Why Round-Robin works well here**: 
Round-Robin guarantees that every application gets frequent, small slices of CPU time. This makes the system appear highly responsive to the user, ensuring that UI inputs like mouse movement and keyboard typing are handled without noticeable lag, even when heavy background tasks are running.

---

## Summary

**Key concepts I understood through these questions:**
1. The architectural differences and memory sharing implications between threads and processes.
2. The mechanics of Round-Robin scheduling, time quanta, and context switching.
3. The complete lifecycle and state transitions of a thread in Java.

**Concepts I need to study more:**
1. More complex scheduling algorithms like Multi-level Feedback Queues.
2. Handling race conditions and thread synchronization in concurrent applications.
