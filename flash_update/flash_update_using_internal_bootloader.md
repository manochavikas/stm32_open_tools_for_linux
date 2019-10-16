# STM32 Flash update: Using internal Bootloader (without st-link)

Stm32 internal bootloader supports flash programming using uart, ic, usb etc. depending on the stm32 device. To execute the bootloader, one has to choose the correct bootmode using boot0/boot1 pins/option bytes.

e.g. for stm32f4,  Boot1=0 & boot0=1 to execute the internal bootloader

![](C:\git_repos\stm32_open_tools_for_linux\images\stm32f4_boot_modes.jpg)

## Dfu/usb to update the flash

dfu-util: Device firmware upgrade utility via usb:  
>git clone git://git.code.sf.net/p/dfu-util/dfu-util  
>./autogen.sh  
>./configure  
>make  
>make install  

Usage:
To write the binary file from micro:
> dfu-util -a 0 -D ../demo_binay_3241g_eval.dfu  

To read the binary file from micro:  
> dfu-util -a 0 -s 0x08000000:1024 -U newfile.bin  

To program the option byte:  
> dfu-util -d 0x0483:0xdf11 -a 1 -s 0x1FFF0010:will-reset -D option_byte_config.bin  

Creating dfu binary:
One quick solution is to use ST application “dfu filemanager” but it is windows based. dfu-suffix, dfu-prefix could be used on linux (didn’t check it)  
You might need to copy “dfu-util/doc/40-dfuse.rules” to “/etc/udev/rules.d” path  
More info @[link to dfu-util](http://dfu-util.sourceforge.net/)

Dfu programming on stm32f417 eval board

![](C:\git_repos\stm32_open_tools_for_linux\images\snapshots\dfu_flash.jpg)

## Bootloader uart/i2c interface to update the flash

stm32flash: device firmware update using serial port or i2c
> git clone https://git.gitorious.org/stm32flash/stm32flash.git  
> make  

Flashing stm32f4:
> ./stm32flash -w filename -v -g 0x0 /dev/ttyS0  
e.g. 
> sudo ./stm32flash -w STM32CubeDemo_STM324xG-EVAL_1.4.0.hex -v -g 0x0 /dev/ttyS0

![](C:\git_repos\stm32_open_tools_for_linux\images\snapshots\stm32flash.jpg)
