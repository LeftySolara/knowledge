# Processes

## What is a process?

A **process** is one of the most fundamental abstractions provided by an OS. It is simply an abstraction by the OS of a running program.

Really, processes are just a bunch of bytes on a disk and the OS gets them running.

## CPU Virtualization

To run multiple processes at once, the OS creates the illusion of there being many CPUs. This way, each process gets its own **virtual CPU**.

The way this works is as follows: the OS runs one process, stops it, runs another process, and so on. This is called **time sharing** and is one method of **virtualizing the CPU**. It allows the OS to run many concurrent processes. Most modern operating systems implement some kind of time sharing.

Time sharing can have a performance cost; each process will run slower if the CPU(s) must be shared.

Operating systems have various scheduling policies to decide which processes run when.

## Machine State

The **machine state** is the set of resources that a process can read or update when it is running.

There are three common resources that make up machine state:

### Memory

In order for a process to run, its instructions and static data must first be loaded into memory. The **address space** of a process is the sections of memory that process can access during its run time,

### Registers

Some CPU registers store important things like the **program counter** (also called the **instruction pointer**), the **stack pointer**, and the **frame pointer**. These are used to track the currently-executing instruction, the stack, function parameters, local variables, and return addresses.

### Storage Devices

Processes will often utilize some resources on physical disk media. For example, most processes keep a list of files that they have open during runtime.

## Process API

The following are some examples of what a basic OS should have regarding interactions with its processes:

- **Creation**: Operating systems should have the ability to create new processes.
- **Destruction**: Operating systems should have the ability to kill processes, especially runaway processes that are not cleaned up properly.
- **Wait**: The ability to wait for a process to stop running.
- **Miscellaneous Control**: Other process controls, such as suspending and resuming
- **Status Check**: The ability to fetch process information such as how long it's been running, the current state, etc.

## Process Creation

This is a list of steps performed that turns a program into a running process:

1. Program code and static data are loaded into memory
2. Memory is allocated for the stack
3. Memory is allocated for the heap
4. Any necessary file descriptors are opened
5. The OS jumps into the `main()` function of the program

Early and simple operating systems load their programs **eagerly**, meaning they do all of these steps at once before running the program. Modern OSes load their programs **lazily**, only loading pieces of the code or data as needed.

## Process States

A process can be in one of three states:

- **Running**: The process is running and executing instructions.
- **Ready**: The process is ready to run but the OS has chosen to not run it at the moment
- **Blocked**: The process has performed some kind of operation that makes it not ready to run until some other thing happens. Examples include waiting for a disk to write and waiting to receive a network packet. When the process is blocked, it stays that way until the other then happens, then it becomes ready again.

A process is said to be **scheduled** when it goes from being ready to actively running. The opposite referred to as the process being **descheduled**.

## Data Structures

The OS is just a program, and thus keep some data structures around to keep track of things. One of these data structures is a **process list** that tracks all processes that are ready and some additional info about them. There's also structures to track blocked processes.

For a more concrete example, check out the `proc` data structure in xv6 or Linux.

## References

- [Operating Systems - Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)