# Debug with openOCD

## Terminal Window 1: start OpenOCD

> openocd -f interface/stlink.cfg -f target/stm32f7x.cfg

![](.\images\snapshots\start_OCD.jpg)  
Loglog file will contain the prints sent via ITM interface to SWO  
Use “tail -f ~/loglog | hexdump” command to see the contents of file loglog at run-time  
Tested on stm32f429 board (version MB1075C), Need to connect PB3 to SWO pin for SWO (connect SB9)  

## Terminal Window2: start gdb

![](.\images\snapshots\start_gdb.jpg)  

> arm-none-eabi-gdb -tui --eval-command="target remote localhost:3333" u-boot
or
> arm-none-eabi-gdb –tui build/Project.elf --eval-command="target remote localhost:3333" --eval-command="monitor reset halt" --eval-command="load"

## Flashing using OpenOCD

> openocd -f interface/stlink-v2-1.cfg -f target/stm32f4x.cfg -c "program u-boot/u-boot.bin exit 0x08000000“

![](.\images\snapshots\flash_using_openOCD.jpg)  

## Terminal Window 3 (optional): Access board using port 4444
Program & other debug stuff:  
> telnet localhost 4444  
> program u-boot.bin 0x08000000 verify  
> mdw 0x08000000  
> help `<string>`  
