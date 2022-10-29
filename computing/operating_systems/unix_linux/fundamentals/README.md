# UNIX Fundamental Concepts

This is a short summary of some fundamental topics regarding UNIX and UNIX-like operating systems. Mode detailed notes can be found be following the links provided in each section.

## The Kernel

The _kernel_ is the central software that manages and allocates computer resources (RAM, CPU, etc.). It is possible to run programs on computers without kernels, but having one makes writing and running programs a lot easier.

On most Linux systems, the kernel resides at `/boot/vmlinuz`. On UNIX, it is commonly found at `/unix`.

### Tasks Performed by the Kernel

This is a non-exhaustive list of common tasks performed by the kernel, in no particular order.

- Process scheduling
- Memory management
- Provision of a file system
- Creation and termination of processes
- Access to devices
- Networking
- Provision of a system call API
- Much more!

### Kernel Mode and User Mode

UNIX systems operate in two modes: kernel mode and user mode. In _user mode_, the CPU can only access memory in user space. In _kernel mode_, the CPU can access memory in user space and kernel space.

## The Shell

The _shell_ is a special-purpose program designed to read commands and execute programs.

For more detailed information, see [this page](./shell.md).

## Users and Groups

In UNIX, each user has a unique account and each account may belong to one or more groups. Each user has a unique username and user ID (called a _uid_). Information about users is stored in the `/etc/passwd` file.

Groups also have unique IDs (called a _gid_) and can contain multiple users.

The _superuser_ is a special account that bypasses all checks on the system, and thus can access any file. It usually has the username `root` with a uid of `0`. This account is often used by system administrators to perform maintenance tasks.

For more detailed information about users and groups, see [this page](./users_groups.md).

## Single-Directory Hierarchy

Some operating systems such as Windows has a directory try for each connected disk. On UNIX systems, this is not the case. UNIX has a single directory tree under which all files, directories, links, devices, etc., reside.

### File Types

All files have a type. The file types available in UNIX are plain text, devices, pipes, sockets, directories, and symbolic links.

### Directories and Links

A _directory_ is a special type of file that consists of a table of filenames and references to those files. The filename-file association is called a _link_. All files have at least one link and may have multiple.

Directories can also contain links to other directories. Every directory has at least two of these: one link to itself (usually signified by a dot `.`) and one link to its parent (usually signified by two dots `..`). The root directory is its own parent.

### Symbolic Links

_Symbolic links_ are alternate names for files. They are special files that contain the name of another file. Usually, the kernel will _dereference_ the link when used in system calls, meaning that the file being pointed to will be used instead of the link itself.

## References

- [The Linux Programming Interface](https://man7.org/tlpi/)
- [Wikipedia - Kernel (Operating System)](<https://en.wikipedia.org/wiki/Kernel_(operating_system)>)
