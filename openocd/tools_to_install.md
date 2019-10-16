# GNU Arm Embeddedd Toolchain
* Install compiler, debugger & other binary utilities  

> wget https://developer.arm.com/-/media/Files/downloads/gnu-rm/8-2019q3/RC1.1/gcc-arm-none-eabi-8-2019-q3-update-linux.tar.bz2?revision=c34d758a-be0c-476e-a2de-af8c6e16a8a2?product=GNU%20Arm%20Embedded%20Toolchain,64-bit,,Linux,8-2019-q3-update -O gcc-arm-none-eabi-8-2018-q4-major  

Link for more info: 
[Arm gnu toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm)  
[Download cortex-M/R toolchain from here](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads)

For ubuntu 16 LTS & older builds, install from launchpad.
Edit etc/apt/sources.list
> deb http://ppa.launchpad.net/team-gcc-arm-embedded/ppa/ubuntu xenial main  
> deb-src http://ppa.launchpad.net/team-gcc-arm-embedded/ppa/ubuntu xenial main  
> sudo apt-get remove gcc-arm-embedded  
> sudo apt-get install gnu-arm-embedded  

# OpenOCD

Download openocd latest release version zip
[Download latest openOCD release](https://sourceforge.net/projects/openocd/files/latest/download)

Or

> git clone: git clone git://git.code.sf.net/p/openocd/code  
> ./bootstrap (only in case of git cloned openocd)  
> ./configure  
> sudo make  
> sudo make install  

Enable st-link hardware for ubuntu : copy the downloaded/cloned file “contrib/99-openocd.rules” to /etc/udev/rules.d/
