<div align="center">
  <h1>Operating System</h1>
</div>

Application software performs specific task for the user.

System software operates and controls the computer system and provides a platform to run application software.

An operating system is a piece of software that manages all the resources of a computer system, both hardware and software, and provides an environment in which the user can execute his/her programs in a convenient and efficient manner by hiding underlying complexity of the hardware and acting as a resource manager.

The operating system provides the means for proper use of the resources in the operation of the computer system.

## Why OS?
1. What if there is no OS?

  - Bulky and complex app. (Hardware interaction code must be in app’s
code base)
  - Resource exploitation by 1 App.
  - No memory protection.
   
2. What is an OS made up of?
  - Collection of system software.

## Function
  - Access to the computer hardware.
  - Interface between the user and the computer hardware
  - Resource management (Aka, Arbitration) (memory, device, file, security, process etc)
      - If every app had its own memory management code, they would become too large. Instead, the OS handles memory management for all apps, keeping them simple. (DRY - Do not Repeat Principle)
  - Hides the underlying complexity of the hardware. (Aka, Abstraction)
  - Facilitates execution of application programs by providing isolation and protection.
      - The OS makes sure that one app cannot access or change another app’s memory, keeping them separate and secure.

## Goals
- Maximum CPU utilization
- Process does not starve
- High Priority Job execution

## Types of OS
1. Single Process OS
   
A single-process operating system is an OS that can execute only one process at a time. This means that it does not support multitasking, where multiple processes run concurrently. Instead, the OS focuses on running a single program until it completes, then moves on to the next task. eg: MS DOS, 

2. Batch Processing OS
   
A Batch Processing Operating System is a type of OS that executes jobs in batches without direct user interaction. It collects jobs, groups them into batches, and processes them sequentially. This system is efficient for tasks that require repetitive execution, such as payroll processing, data analysis, and large-scale computations.

3. Multi Programming OS
   
A Multiprogramming Operating System allows multiple programs (processes) to be loaded into memory and executed concurrently by sharing system resources like CPU and memory. However, only one process runs at a time, while others wait for CPU time. This increases CPU utilization by ensuring it is not idle when a process is waiting for I/O operations.

Multiprogramming increases CPU utilization by keeping multiple jobs (code and data) in the memory so that the CPU always has one to execute in case some job gets busy with I/O.

- Single CPU
- Context switching for processes. (Context switching is the process of saving the state of a currently running process in PCB(Process Control Block) and restoring the state of another process, allowing multitasking in an operating system. It occurs when the CPU switches from one process (or thread) to another.)
- Switch happens when current process goes to wait state.
- CPU idle time reduced.

  
