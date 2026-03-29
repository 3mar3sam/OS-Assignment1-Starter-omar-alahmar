# Development Log

## Instructions
Document your development process as you work on the assignment. Add entries showing:
- What you worked on
- Problems you encountered
- How you solved them
- Time spent

**Requirements**: Minimum 5 entries showing progression over time.

---

## Your Development Log:

### Entry 1 - [March 25, 2026, 3:00 PM]
**What I did**: Set up the project environment and updated my student ID.

**Details**: 
I began by forking the starter repository to my GitHub account and cloning it locally to my machine. I opened the project in VS Code and ensured my Java installation was working properly. The very first code change I made was updating the `studentID` variable on line 175 in `SchedulerSimulation.java` to my actual university ID (445052792). After that, I successfully compiled and ran the base simulation.

**Challenges**: 
I had some initial issues getting VS Code to link properly with my GitHub account, as it kept asking for credentials.

**Solution**: 
I solved this by logging out of the GitHub extension and logging back in using the browser authentication method, which properly linked my university email account.

**Time spent**: 45 minutes

---

### Entry 2 - [March 26, 2026, 4:30 PM]
**What I did**: Implemented Feature 1: Process Priority.

**Details**: 
I modified the `Process` class by adding a `private int priority` field. I updated the constructor to accept the priority as a parameter and added a `getPriority()` getter method. Then, in `SchedulerSimulation.java`, I added logic to generate a random priority between 1 and 5 when instantiating new processes. Finally, I updated the `addProcessToQueue` method to display the priority of the process when it gets added to the ready queue.

**Challenges**: 
I had to make sure the random number generator for priority was inclusive between 1 and 5, as `random.nextInt(5)` gives 0 to 4.

**Solution**: 
I added 1 to the result (`random.nextInt(5) + 1`), ensuring the priorities strictly fell into the 1-5 range required by the assignment specs.

**Time spent**: 1 hour

---

### Entry 3 - [March 27, 2026, 5:00 PM]
**What I did**: Implemented Feature 2: Context Switch Counter.

**Details**: 
To track context switches, I created a `public static int contextSwitches = 0;` variable at the top of the `SchedulerSimulation` class. Inside the `main` method's `while (!processQueue.isEmpty())` loop, I added an increment operation (`contextSwitches++`) right before the `currentThread.start()` invocation. I then added a console output statement at the very end of the simulation to display the total number of context switches.

**Challenges**: 
I was initially unsure exactly where a "context switch" should be counted—whether it was when a process stops or when a new process starts.

**Solution**: 
After reviewing the lecture notes on OS context switching, I realized that starting any process from the queue to run on the CPU essentially represents the scheduler switching context to that process. Thus, putting the counter increment right before execution was the most accurate place.

**Time spent**: 40 minutes

---

### Entry 4 - [March 28, 2026, 2:15 PM]
**What I did**: Implemented Feature 3: Waiting Time Tracking.

**Details**: 
I added `creationTime` and `completionTime` fields to the `Process` class. `creationTime` is captured via `System.currentTimeMillis()` in the constructor. `completionTime` is set when a process finally finishes (either by `runToCompletion()` or when remaining time reaches 0). I created a `getWaitingTime()` method using the formula: `(completionTime - creationTime) - burstTime`. Lastly, I maintained a separate list `allProcesses` to be able to iterate through all processes at the end to print the summary table.

**Challenges**: 
Calculating waiting time correctly was tricky because threads execute continuously in segments. It took me a moment to realize I could just use the overall turnaround time minus the burst time.

**Solution**: 
Instead of tracking waiting time granularly each time a thread is in the queue, I just took the timestamp when the thread started and when it completely died, subtracted the processing burst time, and got the waiting time seamlessly.

**Time spent**: 1.5 hours

---

### Entry 5 - [March 29, 2026, 7:00 PM]
**What I did**: Testing, Documentation, and Final Polish.

**Details**: 
I thoroughly tested the completed application multiple times to ensure the outputs were consistent and looked appropriate with the ANSI color codes. I populated the `ANSWERS.md` file by thoughtfully explaining threads vs. processes, thread states, and Round-Robin applications. I filled out this `DEVELOPMENT_LOG.md` file and completed the `REFLECTION.md` file. I then made sure to commit all the latest changes and ensure the repository was public.

**Challenges**: 
Writing precise and technically sound answers for `ANSWERS.md` required a quick refresher on some of the core textbook materials regarding Round Robin.

**Solution**: 
I referenced the OS textbook chapter on CPU Scheduling to make sure my explanation of the ready queue behavior and fairness was academically sound.

**Time spent**: 2 hours

---

## Summary

**Total time spent on assignment**: Approx. 6 hours

**Most challenging part**: 
Understanding the thread lifecycle and where to accurately mark the timestamps so that the waiting time calculation worked correctly without breaking the thread execution simulation logic.

**Most interesting learning**: 
Observing how the threads context-switch on standard console output really visualized the Round-Robin algorithm for me. Actually seeing "P3 yields CPU" helped me bridge the gap between abstract textbook theory and practical Java code.

**What I would do differently next time**: 
Next time, I'd probably write the summary table formatting code alongside testing the waiting time. Doing it cleanly with `System.out.printf` took extra time that could have been saved with a slightly more meticulous upfront design.