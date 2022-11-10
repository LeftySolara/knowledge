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

## Memory Layout of a Process

## Virtual Memory Management

## Links

- [The Linux Programming Interface](https://man7.org/tlpi/)
- [Process (Computing) - Wikipedia](<https://en.wikipedia.org/wiki/Process_(computing)>)
