# GDB

GDB is a great command-line debugging tool, which I use for all of my C/C++ projects.

## Commands

Set a breakpoint at the beginning of `main`:

```text
(gdb) b main
```

Set a breakpoint at a line in the current file:

```text
(gdb) b 35
```

List breakpoints:

```text
(gdb) info b
```

Delete a breakpoint:

```text
(gdb) delete 2
```

## Run a program until segfault

```
set pagination off
break exit
commands
run
end
```

## Debugging NCURSES Programs

To debug an NCURSES program, its output needs to be redirected to a different tty. This allows the program to continue running nicely alongside our debugging session.

The following are steps for setting up a debugging session:

1\) Open two tty sessions. One will be for running gdb and the other will run the ncurses program. We'll call the first tty the _debugging shell_ and the second the _program shell_.

2\) Find the device file of the program shell with the `tty` command. We'll use this to redirect the output, as mentioned previously.

3\) In the debugging shell, start gdb as normal.

4\) In gdb, run `tty <device file>`, where the device file is the one found in step 2. This tells gdb to redirect the program's I/O to the program shell.

5\) In the program shell, run the `sleep` command for at least as long as the debugging session will last. This ensures that all input goes to the program rather than the shell behind it.

6\) In the debugging shell, run the program and debug as normal.

