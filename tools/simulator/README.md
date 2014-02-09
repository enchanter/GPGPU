This is a instruction accurate functional simulator for this instruction set.  It is not
cycle accurate, and it does not simulate the behavior of caches. It can run in a few
different modes, specified with the -m &lt;mode&gt; flag:
- cosim -it runs in co-simulation mode.  It reads instruction
side effects from stdin (which are produced by the Verilog model) and 
verifies they are correct given the program.
- debug - Allows single step, breakpoints, etc.  This is currently not functional.
- gui - (Mac only) Pops up a window that displays the live contents of the framebuffer
- &lt;default&gt; Normal mode runs from the command line.

The simulator expects a memory image as input, encoded in hexadecimal in a format that is 
consistent with that expected by the Verilog $readmemh.  This can be produced from an ELF
file by using the elf2hex utility included with the toolchain project.

The simulation will exit when all threads are halted (by disabling using control registers)

When the simulation is finished, it can optionally dump memory with the -d option, which takes 
parameters filename,start,length

Adding the -v (verbose) flag will dump all register and memory transfers to standard out.

The simulator allocates 5Mb of memory to the virtual machine, starting at address 0.

