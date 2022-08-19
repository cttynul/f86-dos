# Faux86
_A portable, open-source 8086 PC emulator for bare metal Raspberry Pi_

Faux86 is designed to be run **bare metal** on a Raspberry Pi. This means that the emulator runs directly on the hardware so no OS needs to booted on the Pi. 

## Features
* 8086 and 80186 instruction set emulation
* CGA / EGA / VGA emulation is mostly complete
* PC speaker, Adlib and Soundblaster sound emulation
* Serial mouse emulation

## Installation
1. [**Download** Release](https://github.com/cttynul/faux86/releases) or built by yourself.
2. Flash it on a small SD card using **Balena Etcher** or **Win32DiskImager**
3. Profit

## Usage with Raspberry Pi
By default Faux86 boots from a floppy image `dosboot.img`, and filename is hardcoded in `kernel.cpp`

Since MS-DOS is accessing the SD card directly, it does not work for large SD card types. I have found the best solution is to use a small capacity SD card and flash the image as a 32MB card.

USB keyboard and mouse should be plugged in before booting - hot swapping of devices is not supported.

### Partition scheme
* `A:\` MS-DOS Read-Only floppy image.
* `C:\` SD card; system file, kernel, etc, files are hidden to make partition easier to be browsed.
* `D:\` Any attached mass storage device.

### MS-DOS 6.22
MS-DOS 6.22 it's loaded from `dosboot.img` floppy image, with some out-of-the-box customiztion you may like to know:
* `C:\AUTOEXEC.BAT` you can easly _edit it using edit_; that's the main reason why I forked this repo.
* `PATH` All executables included into MS-DOS floppy drive are in PATH.

### MS-DOS EXEs
If you're too lazy to Google them here's a list of what's included
* `ATTRIB.EXE`
* `CHKDSK.EXE`
* `DEBUG.EXE`
* `EDIT.EXE`
* `EXPAND.EXE`
* `FDISK.EXE`
* `FORMAT.EXE`
* `KEYB.COM`
* `MOUSE.COM` Run at boot with `C:\AUTOEXEC.BAT`
* `QBASIC.EXE`

## Compatibility
* Raspberry Pi [A, B, A+, B+]
* Raspberry Pi 2 [B]
* Raspberry Pi 3 [A+, B, B+]
* Raspberry Pi Zero

_Where're Raspberry PI 4 and Raspberry PI 400?_

I've never bought a PI 4 and/or the _Commodre-Vibes_ PI400; so can't test it all but someone on RaspberryPi forum do that! Here're all links:
* [RPI4/RPI400 Kernel](https://drive.google.com/file/d/1WlZcO4mXQQpHD_EJ4URIEJmqHPTugFCk/view) by **jepalza**

## Credits
Faux86 was originally based on the Fake86 emulator by Mike Chambers. 
http://fake86.rubbermallet.org
A lot of the code has been shuffled around or rewritten in C++ but the core CPU emulation remains mostly the same.

Faux86 uses the Circle library to interface with the Raspberry Pi
https://github.com/rsta2/circle



  
