# [GDB](https://www.gnu.org/software/gdb/)

GDB is a great command-line debugging tool, which I use for all of my C/C++ projects.

## Commands

Set a breakpoint at the beginning of `main`:
```
(gdb) b main
```

Set a breakpoint at a line in the current file:
```
(gdb) b 35
```

List breakpoints:
```
(gdb) info b
```

Delete a breakpoint:
```
(gdb) delete 2
```


## Debugging NCURSES Programs

To debug an NCURSES program, its output needs to be redirected to a different tty. This allows the program to continue running nicely alongside our debugging session.

The following are steps for setting up a debugging session:

1) Open two tty sessions. One will be for running gdb and the other will run the ncurses program.  We'll call the first tty the *debugging shell* and the second the *program shell*.

2) Find the device file of the program shell with the `tty` command. We'll use this to redirect the output, as mentioned previously.

3) In the debugging shell, start gdb as normal.

4) In gdb, run `tty <device file>`, where the device file is the one found in step 2. This tells gdb to redirect the program's I/O to the program shell.

5) In the program shell, run the `sleep` command for at least as long as the debugging session will last. This ensures that all input goes to the program rather than the shell behind it.

6) In the debugging shell, run the program and debug as normal.