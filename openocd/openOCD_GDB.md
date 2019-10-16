# OpenOCD
OpenOCD provides two access points:

* GDB 	: to debug the source code, available for application processor as
  well as microcontrollers.
* Telnet Server : controls like flash writing

![OpenOCD Image](C:\git_repos\stm32_open_tools_for_linux\images\openOCD.JPG)

OpenOCD can be used to debug remote targets as it complies with thr remote gdbserver protocol.

Launching OpenOCD server:
e.g. for stm32f7: 
> openocd -f interface/stlink.cfg -f target/stm32f7x.cfg

Program & other debug stuff:  
> telnet localhost 4444
> program u-boot.bin 0x08000000 verify

> mdw 0x08000000

> help `<string>`

More info : http://www.openocd.net/


# GNU Debugger (GDB)
GDB works with server, allows to:
* Start the program
* Break the program.
* Examine the system (registers, variables, functions etc)
* Modify the system parameters to quick test
* Re-run the software
* Provides “Remote debugging” to debug embedded systems

Common commands:
* gdb program.elf : Launch the program
* run
* print
* info frame
* next or n
* stepi
* break function_name
* continue or c

More info at : https://www.gnu.org/software/gdb/


