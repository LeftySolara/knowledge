# Processes

A **process** is an instance of a running program. A **program** is a file containing information that describes how to construct a process at runtime.

Programs consist of the following information:

- _binary format identification_: metainformation describing the format of an executable file
  - most UNIX implementations use the ELF format
- machine-language instructions
- the program entry-point address
- data (specifically, values for initializing variables and constants)
- _symbol and relocation tables_: describe locations and names of functions and variables
- shared-library and dynamic linking information
  - includes information about shared libraries required to run the program and the path of the needed dynamic linker
- various other information

One program may construct many processes. In other words, multiple instances of the same program may be running at once.

## Process IDs

A **process ID** (PID) is a positive integer that uniquely identifies a process. Every process has a process ID, which used and returned by a variety of system calls.

There is no fixed relationship between a program and the PID of the process created to run it. In other words, the PID assigned to a process has nothing to do with the specific program being run. There are a few exceptions to this, particularly that the `init` process always has PID 1.

In Linux, the `getpid()` system call can be used to fetch the PID of a process.

The Linux kernel limits PIDs to values less than or equal to 32,767. On 64-bit systems, this can be adjusted up to ~4 million. When a new process is created it is assigned the next sequentially available PID. If the 32,767 limit is reached, then the PID counter resets and starts using lower values again. During this reset, the counter resets to 300, not 1, since lower-number PIDs are usually in use by the system.

### Parent Processes

Every process has a **parent**, which is the process the created it. If a parent process is terminated, the child process is then adopted by `init`.

The PID of a parent process can be obtained using the `getppid()` system call.

## Memory Layout of a Process

Memory allocated to a process is composed of parts called **segments**. This section describes each segment type.

The _text segment_ consists of the machine-language instructions of the program being run. It is read-only so the program doesn't overwrite itself. This segment is sharable, so multiple processes can map to a single copy of the program. This helps save memory as each process does not need to keep its own copy of the instructions.

The _initialized data segment_ contains global and static variables that are explicitly initialized. These are read from the executable when the program is loaded into memory.

The _uninitialized data segment_ contains global and static variables that are not explicitly initialized. All memory in this segment is initialized to `0`.

The _stack_ holds stack frames. A stack frame stored a function's variables, arguments, and return value. One frame is allocated for each currently-called function. The stack dynamically grows and shrinks as needed.

The _heap_ is an area in which memory can be dynamically allocated at runtime.

## Virtual Memory Management

## Links

- [The Linux Programming Interface](https://man7.org/tlpi/)
- [Process (Computing) - Wikipedia](<https://en.wikipedia.org/wiki/Process_(computing)>)
