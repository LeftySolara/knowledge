
# CPU Virtualization

To virtualize a CPU, an OS needs to share the physical CPU among many jobs. The basic idea is that one process runs for a while, then another runs, and so on. This is called **time sharing**.

There are two challenges that come along with this:

1. How can we implement virtualization without adding excessive overhead to the system?
2. How do we run processes effectively while maintaining control over the CPU?

These two questions are addressed by a mechanism called **Limited Direct Execution**.

## Limited Direct Execution

Limited Direct Execution is a fairly basic technique. The "direct execution" part simply means "run the process directly on the CPU". Because processes are running directly on the CPU, their performance is very fast.

There are two problems that need to be solved here:

1. How can we prevent user processes from doing things they aren't supposed to?
2. How can the OS regain control of the CPU so that it can switch between processes?

Below are some possible answers to these questions.

### Restricted Operations - System Calls

User processes are run in what is referred to as **user mode**, while the OS operates in **kernel mode**. In user mode, processes are restricted in what they can do, such as performing I/O. In kernel mode, a process is unrestricted and can do whatever it pleases.

So then, how does a user process do things such as disk I/O and other restricted operations? The answer is system calls. A **system call** allows the kernel to carefully expose certain key pieces of functionality to user programs. It is a request to the OS to do something. This way, user programs can do what they need while still being restricted.

To specify system calls, each call is usually assigned a **system call number**. The user program is responsible for placing the desired number in a register or a specific location on the stack. The OS will read this number, verify it is valid, and then execute the corresponding code.

System calls work by executing special instructions called **trap** instructions. A trap instruction makes execution jump into the kernel and raises the privilege level to kernel mode. To return to user mode and the user program, a **return-from-trap** instruction is executed.

To be able to return correctly from a trap, the computer's hardware must save a certain amount of the process's registers. This information is stored on the per-process **kernel stack**. The return-from-trap will pop these values off of the stack to resume execution of the user-mode program.

This begs the question: how does a trap instruction know which code to execute? One possible answer is letting the calling process specify an address to jump to. This is a **Very Bad Idea**. Such a thing would allow a process to access any part of the system and possibly take over the whole thing.

The way it actually works is thus: at boot time the OS sets up a **trap table** which maps services to functions called **trap handlers**. These handlers execute the actual code of the requested service. Also during boot time, the OS tells the hardware the locations of the trap handlers.

### Switching Between Processes

If a user process is running on the CPU, then the OS is not. The OS needs a way to regain control of the CPU in order to switch between processes. Below are two possible approaches to this problem.

#### Cooperative: Wait for System Calls and Illegal Operations

With this approach, the OS trusts user processes to behave reasonably. For example, it's assumed that long-running processes will periodically give up the CPU so the OS can do its thing.

Processes would return control to the OS by using system calls. Some systems might even have an explicit `yield()` system call that does nothing but return control to the OS.

Control would also be returned when an illegal operation occurs (ex. dividing by zero). The operation would generate a trap into the OS.

The problem with this approach is what happens when a user process is malicious or gets stuck in an infinite loop? The only recourse would be to reboot the entire machine.

#### Non-cooperative: The OS Takes Control

With this approach, the OS takes control of the CPU by utilizing **timer interrupts**.

Basically, a timer can be programmed to raise an interrupt every few milliseconds. When this interrupt is raised, the currently-running process is halted and a pre-configured **interrupt handler** in the OS runs. At that point the OS is in control and can do whatever it needs.

During boot, the OS informs the hardware which code to run when the interrupt occurs. It also starts the timer.

When an interrupt occurs, the hardware has a bit of responsibility: It must save enough of the state of the program so that the return-from-trap will be able to resume the process correctly.

##### Saving and Restoring Context

When the OS regains control, it must decide whether to continue running the already-running process or switch to a different one. This decision is made by a part of the OS called a **scheduler**.

If the OS decides to switch processes, it performs what is known as a **context switch**. During this event, the OS saves register values from the currently-executing process and restores registers from the soon-to-be-running process. This ensures that when the return-from-trap triggers, the system executes the new process rather than the old one.

## References

- [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)