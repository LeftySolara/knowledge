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

This begs the question: what interfaces should an OS present for process creation can control? On UNIX systems, those interfaces consist of the following:

### The `fork()` System Call

The `fork()` system call is useful for creating new processes. The way it works is a follows:

Every process has a **process identifier (PID)**, a name we can use when we want to control it. When `fork()` is called, it creates a _new_ process with its own PID. This new process also has its own copy of the process's address space, its own registers, etc. It is an _almost_ exact copy of the calling process.

The new process is called the **child**, while the original process is called the **parent**. After the call to `fork()`, the child process receives a return code of 0 and the parent receives a return code of the child's PID.

When the child process runs, it does not start at `main()`. Instead, it starts at the same location where `fork()` was called.

Either the child or parent can run after the `fork()` is called. That is determined by the **CPU scheduler**.

**TODO**: Add example code that uses the `fork()` system call.

### The `wait()` System Call

The `wait()` system call is useful if you want to make a process wait for another process to finish. When called after a `fork()`, it makes the parent process suspend execution until the child has finished running.

**TODO**: Add example code that uses the `wait()` system call.

### The `exec()` System Call

The `exec()` system call (and its variants) are useful if you want to run a program that is different from the calling program.

`exec()` does _not_ create a new process. Instead it takes the name of an executable, loads code and static data from it, and overwrites its current code segment with it; the stack, heap, and other parts of program memory are re-initialized. It essentially transforms a currently-running program into a different running program.

A successful call to `exec()` never returns.

**TODO**: Add example code that uses the `exec()` system call (or one of its variants).

###  Output Redirection, Pipes, and "The Why"

Why do we use such an odd interface for simple process creation?

The answer is that the separation of `fork()` and `exec()` are essential in building a UNIX shell. It allows the shell to run code _after_ the call to `fork()` but _before_ the call to `exec()`. This code could alter the environment of the program that is about to run.

Remember, the shell is just a user program. When you interact with it, it performs the following steps:

1. Display a prompt
2. Wait for user input
3. Call `fork()` to create a new process for running the given command
4. Call some variant of `exec()` to run the command
5. Wait for the command to complete by using `wait()`

The separation of `fork()` and `exec()` also allow the shell to do a number of useful things like **output redirection**. Take the following command as an example:

```
prompt> wc hello.c > newfile.txt
```

Here, the output of `hello.c` is redirected to `newfile.txt`. How does this work? When the child process is created, before calling `exec()`, the shell closes **standard output** and opens `newfile.txt`. By doing this, any output from `wc` is sent to the file.

This works because of a particular behavior in UNIX systems. They start looking for free file descriptors starting at 0 (which is standard output). If you close 0, then it checks for 1, then 2, and so on until it finds an open one. In this case, the open one is our file.

**Pipes** are implemented in a similar way, except with the `pipe()` system call. Output of one process is connected to an in-kernel pipe (basically, a queue) and the input of another process is connected to that same pipe. Thus, the output of one process is used as input to the next.

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
- [The Linux Programming Interface](https://man7.org/tlpi/)
- [Process (Computing) - Wikipedia](<https://en.wikipedia.org/wiki/Process_(computing)>)