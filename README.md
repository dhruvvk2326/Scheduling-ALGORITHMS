# CPU-Scheduling-Algorithms

An implementation of various CPU scheduling algorithms in C++. The algorithms included are First Come First Serve (FCFS), Round Robin (RR), Shortest Process Next (SPN), Shortest Remaining Time (SRT), Highest Response Ratio Next (HRRN), Feedback (FB) and Aging.

## Table of Contents

- [CPU-Scheduling-Algorithms](#cpu-scheduling-algorithms)
  - [Algorithms](#algorithms)
    - [First Come First Serve (FCFS)](#first-come-first-serve-fcfs)
    - [Round Robin with varying time quantum (RR)](#round-robin-with-varying-time-quantum-rr)
    - [Shortest Process Next (SPN)](#shortest-process-next-spn)
    - [Shortest Remaining Time (SRT)](#shortest-remaining-time-srt)
    - [Highest Response Ratio Next (HRRN)](#highest-response-ratio-next-hrrn)
    - [Feedback (FB)](#feedback-fb)
    - [Feedback with varying time quantum (FBV)](#feedback-with-varying-time-quantum-fbv)
    - [Aging](#aging)
  - [Installation](#installation)
  - [Input Format](#input-format)
  - [Contributors](#contributors)

## Algorithms

### First Come First Serve (FCFS)

- First Come First Served (FCFS) is a scheduling algorithm where the first arriving process is executed first. It is straightforward but can result in inefficiency if there are processes with long execution times. FCFS lacks prioritization mechanisms, making it a non-preemptive algorithm. In FCFS scheduling, regardless of burst time or priority, the earliest arriving process is given precedence. This can lead to inefficiencies as longer processes may delay shorter ones. FCFS finds common use in batch systems where process order is critical.

### Round Robin with varying time quantum (RR)

-Round Robin (RR) with a variable quantum is a CPU scheduling algorithm that employs time-sharing to allocate CPU time among processes. Unlike traditional RR, this version adjusts the quantum (time slice) dynamically based on process requirements. This flexibility allows shorter burst time processes to receive smaller quanta, while longer ones can be allotted larger quanta.

-The algorithm operates by managing a queue of processes, where each process receives a quantum of CPU time for execution. When a process's quantum expires, it moves to the end of the queue, and the next process in line receives its turn.

-The use of a variable quantum enhances efficiency by optimizing CPU utilization. Shorter processes benefit from more frequent CPU access, reducing their waiting times. Moreover, this approach mitigates the risk of starvation, where long-running processes monopolize CPU resources and hinder others from executing.

### Shortest Process Next (SPN)

-Shortest Process Next (SPN) is a scheduling algorithm that prioritizes processes based on their burst time, which is the time required to complete their task. It operates in a non-preemptive manner, meaning once a process begins execution, it continues until it finishes or enters a waiting state.

-The algorithm manages a queue of processes upon their arrival, assigning each a burst time. Processes are sorted in ascending order of their burst times, with the shortest burst time process being executed first. New arrivals are inserted into the queue and sorted accordingly, ensuring the process with the shortest burst time remains at the front and is next to execute.

-SPN proves advantageous in scenarios aiming to minimize the average waiting time for processes. By prioritizing shorter processes, it reduces their queue wait times. However, longer processes may face delays behind shorter ones, potentially impacting overall system performance.

-To summarize, SPN prioritizes process execution based on burst time, operates in a non-preemptive manner, and is favored in contexts where minimizing average process waiting times is crucial.

### Shortest Remaining Time (SRT)

-Shortest Remaining Time Next (SRT) is a scheduling algorithm similar to Shortest Process Next (SPN) but operates as a preemptive algorithm. This means that once a process begins execution, it can be interrupted by a new process with a shorter remaining execution time.

-The algorithm maintains a queue of processes where each process is assigned a burst time upon arrival. Processes are sorted based on their remaining execution time, with the process having the shortest remaining time being executed first. New arrivals are added to the queue and prioritized accordingly, ensuring that the process with the shortest remaining time remains at the front for the next execution.

-SRT proves advantageous in scenarios aiming to minimize the average waiting time for processes, as it prioritizes shorter processes and reduces their queue waiting times. Moreover, it adapts well to situations where burst times are uncertain, adjusting dynamically to changes in remaining execution times during process execution.

-In summary, SRT prioritizes process execution based on remaining time, operates preemptively by potentially interrupting ongoing processes, and is favored in contexts where minimizing average process waiting times is crucial and burst times are unpredictable.

### Highest Response Ratio Next (HRRN)

-Highest Response Ratio Next (HRRN) is a scheduling algorithm that prioritizes processes based on their response ratio. It operates non-preemptively, meaning once a process begins execution, it continues until completion or enters a waiting state.

-The response ratio is determined by the ratio of a process's waiting time to its burst time. Processes are sorted in descending order of their response ratios, with the highest ratio process being executed first. As new processes arrive, they are added to the queue and prioritized based on their response ratios, ensuring that the process with the highest ratio remains at the forefront for execution.

-HRRN is advantageous in scenarios focused on minimizing the average waiting time for processes, as it gives priority to processes with longer waiting times, reducing their queue wait durations. It also adapts well to scenarios where burst times are unpredictable, adjusting dynamically based on changes in waiting times during process execution.

-To summarize, HRRN prioritizes process execution based on response ratios, operates in a non-preemptive manner, and is preferred in situations aiming to minimize average process waiting times, especially when burst times are uncertain.

### Feedback (FB)

-The Feedback scheduling algorithm allocates CPU time to processes based on their priority levels, utilizing multiple priority queues in a multi-level priority system.

-Processes with higher priority levels are given precedence for execution. As new processes arrive, they are placed into the appropriate priority queue based on their assigned priority level. Upon completion of execution, a process is demoted to the next lower priority queue.

-This algorithm proves advantageous in environments managing a diverse mix of processes, including those of varying durations and priority levels. Through its use of multiple priority queues, it ensures higher-priority processes are executed promptly while allowing lower-priority processes the opportunity to execute over time.

-To summarize, Feedback is a multi-level priority scheduling algorithm that manages CPU allocation based on priority levels, utilizing distinct priority queues. It prioritizes higher-priority processes for immediate execution and is well-suited for environments handling a variety of process types and priorities.

### Feedback with varying time quantum (FBV)

- Same as [Feedback](#feedback-fb) but with varying time quantum.
- Feedback with varying time quantum also uses multiple priority queues and assigns a different time quantum for each priority level, it allows the algorithm to be more efficient by spending more time on higher-priority processes and less time on lower-priority processes.

### Aging

-Xinu is an operating system developed at Purdue University. Its scheduling policy ensures that the highest priority process eligible for CPU service is always executing, utilizing round-robin scheduling for processes of equal priority. However, this approach can lead to starvation for lower-priority processes, as they may never receive CPU time when higher-priority processes are consistently eligible for execution.

-To mitigate starvation, Xinu employs an aging scheduler strategy. During each rescheduling operation (such as a timeout), the scheduler increments the priority of all ready processes by a constant value. This prevents processes from being continuously passed over by ensuring that each process in the ready state eventually reaches the highest priority level.

-Upon each invocation of the scheduler, several steps are taken: the current process's priority is set to its initial assigned value, all other ready processes have their priorities incremented by 1, and the scheduler selects the highest priority process from the pool of eligible processes.

-It's important to note that during each scheduler call, the entire list of ready processes needs to be traversed to determine the highest priority process for execution.

## Installation

1- Clone the repository

2- Install g++ compiler and make

```bash
scoop install main/make
scoop install main/gcc
```

3- Compile the code using `make` command

4- Run the executable file ./lab.exe

## Input Format

- Line 1: "trace" or "stats"
- Line 2: a comma-separated list telling which CPU scheduling policies to be analyzed/visualized along with
  their parameters, if applicable. Each algorithm is represented by a number as listed in the
  introduction section and as shown in the attached testcases.
  Round Robin and Aging have a parameter specifying the quantum q to be used. Therefore, a policy
  entered as 2-4 means Round Robin with q=4. Also, policy 8-1 means Aging with q=1.

1.  FCFS (First Come First Serve)
2.  RR (Round Robin)
3.  SPN (Shortest Process Next)
4.  SRT (Shortest Remaining Time)
5.  HRRN (Highest Response Ratio Next)
6.  FB-1, (Feedback where all queues have q=1)
7.  FB-2i, (Feedback where q= 2i)
8.  Aging

- Line 3: An integer specifying the last instant to be used in your simulation and to be shown on the timeline.
- Line 4: An integer specifying the number of processes to be simulated.
- Line 5: Start of description of processes. Each process is to be described on a separate line. For algorithms 1 through 7, each process is described using a comma-separated list specifying:

  1- String specifying a process name\
   2- Arrival Time\
   3- Service Time

- **Note:** For Aging algorithm (algorithm 8), each process is described using a comma-separated list specifying:

  1- String specifying a process name\
   2- Arrival Time\
   3- Priority

- Processes are assumed to be sorted based on the arrival time. If two processes have the same arrival time, then the one with the lower priority is assumed to arrive first.
