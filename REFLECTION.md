# Reflection Questions

## Instructions
Answer the following questions about your learning experience. Each answer should be **at least 5-7 sentences** and show your understanding.

---

## Question 1: What did you learn about multithreading?

**Your Answer:**
Through this assignment, I learned that multithreading allows a single program or application to execute multiple tasks concurrently, sharing the same memory space efficiently compared to separate, heavy system processes. I saw firsthand how a `Thread` starts in the 'New' state, transitions to 'Runnable' upon calling `.start()`, and is managed by an underlying scheduler structure. It was completely eye-opening to see how unpredictable the order of raw thread execution might be unless an algorithm like the Round-Robin queue imposes explicit constraints. Furthermore, working directly with `.()` and `.sleep()` elucidated how synchronization works; pausing current execution contexts safely while letting another thread utilize the CPU resource sequentially ensures no overlap occurs in this simulation context. Ultimately, I better understand the trade-offs in resource allocation when handling numerous tasks simultaneously within an OS framework.

---

## Question 2: What was the most challenging part of this assignment?

**Your Answer:**
The most challenging part was unquestionably implementing the logic for the context switch counter and accurately tracking the waiting time. At first glance, understanding where to insert the counter increment seemed trivial, but doing so right before the task resumed operation (or after yielding) required a thorough grasp of the `Runnable` lifecycle loop happening in `main()`. Furthermore, calculating the actual waiting time involved tracking logic that I had never attempted before, namely capturing system epoch timestamps during `Process` instantiation and again upon actual termination. Tracking `System.currentTimeMillis()` at accurate spots without throwing the simulation off-balance when doing iterative looping proved demanding. Eventually, applying the correct formula mapping overall lifespan to burst time simplified my struggles immensely, translating theoretical CPU burst calculations into practical code.

---

## Question 3: How did you overcome the challenges you faced?

**Your Answer:**
I approached solving these challenges methodically by consulting the provided course textbook chapters on CPU scheduling, particularly the sections thoroughly detailing turnaround time and waiting time calculations. Whenever I was stuck or my logic resulted in incorrect times, I would inject multiple `System.out.println()` debug statements in different parts of the thread lifecycle (upon queuing, resuming, and termination). Doing so painted a clear picture in the console output of precisely when variables updated in memory. I also reviewed online documentation for the Java `Thread` class and its specific timing functionalities to ensure my use of `System.currentTimeMillis()` wasn't accidentally drifting during thread sleep periods. Breaking the task down logically into specific checkpoints—where each modification was independently verified—allowed me to overcome the overarching complexity with confidence.

---

## Question 4: How can you apply multithreading concepts in real-world applications?

**Your Answer:**
Multithreading concepts are profoundly applicable in modern-day computing applications like web browsers and complex interactive video games. In web browsers, executing tasks in individual threads ensures that a single hanging script on one browser tab does not cause the entire application window to freeze and stop responding to keyboard strokes or mouse inputs. Another direct application is within multiplayer online games, where client input processing, graphics rendering, and server packet communication all utilize independent concurrent threads. Because a game cannot wait sequentially for a ping reply to draw the next frame, threading ensures seamless graphical output concurrently alongside networking operations. Fundamentally, everything we interact with smoothly in the digital era owes its responsiveness to adeptly managed thread architectures preventing bottlenecks.

---

## Additional Reflections (Optional)

### What would you like to learn more about?
I am curious about the prevention of deadlock situations and how Java specifically handles highly contested shared data locks across dozens of threads using objects like `ReentrantLock` or `ConcurrentHashMap`.

---

### How confident do you feel about multithreading concepts now?
**Intermediate**

I feel much more comfortable designing sequential logic using `Runnable` and capturing states. However, handling deep race conditions and complex `synchronized` blocks against actual shared mutable data without arbitrary queue gating still feels like a topic requiring substantially more practice and study.

---

### Feedback on the assignment
This assignment was highly insightful because it perfectly bridged OS theory algorithms with tangible software implementation. Simulating CPU scheduler queue mechanics entirely from scratch utilizing explicit language threading constructs effectively cemented my understanding of how low-level hardware constraints manifest dynamically.