# F86-DOS
_Powered by Faux86: A portable, open-source 8086 PC emulator for bare metal Raspberry Pi_

**F86-DOS** is an "_Operating System_" powered by **Faux86** designed to be run **bare metal** on a Raspberry Pi. This means that the emulator runs directly on the hardware so no OS needs to booted on the Pi. 

## Features
* 8086 and 80186 instruction set emulation
* CGA / EGA / VGA emulation is mostly complete
* PC speaker, Adlib and Soundblaster sound emulation
* Serial mouse emulation

## Installation
1. [**Download** Release](https://github.com/cttynul/f86-dos/releases)
2. Flash it on a small SD card using **Balena Etcher** or **Win32DiskImager**
4. Profit

## Usage with Raspberry Pi
By default Faux86 boots from a floppy image `dosboot.img`, and filename is hardcoded in `kernel.cpp`

Since MS-DOS is accessing the SD card directly, it does not work for large SD card types. I have found the best solution is to use a small capacity SD card and flash the image as a 32MB card.

USB keyboard and mouse should be plugged in before booting - hot swapping of devices is not supported.

### Partition scheme
* `A:\` MS-DOS Read-Only floppy image.
* `C:\` SD card; system file, kernel, etc, files are hidden to make partition easier to be browsed.
* `D:\` Any attached mass storage device.

### Features
MS-DOS boot up from `dosboot.img` floppy image, with some out-of-the-box customiztion you may like to know:
* `C:\AUTOEXEC.BAT` you can easly _edit it using edit_; that's the main reason why I forked this repo.
* `PATH` All executables included into MS-DOS floppy drive are in PATH.
* `KEYBOARD.SYS` Missing layout definition.

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

I've never bought a PI 4 and/or the _Commodre-Vibes_ PI400; so can't test it all but **jepalza** did and released binaries on Raspberry PI Official Forum! 
* [Download](https://drive.google.com/file/d/1WlZcO4mXQQpHD_EJ4URIEJmqHPTugFCk/view) - The one originally published by **jepalza** | *drive.google.com*
* [Download](https://github.com/cttynul/f86-dos/tree/master/build/pi4) - The mirror on this repository | *github.com*

By the way if you got an **RPI4** I suggest you to install [**DOSBox**](https://www.dosbox.com/) on **RaspberryOS** (*formerly Rasbian*) and make it start at boot; Faux86 is not able to run anything compiled for **386** architecture and it official support up to **186**; instead of DOSBox that can run over the **98%** of *DOS-Softeca*.

## My Setup
I mainly forked originally repository cause of many software-related lack of features I've already mantioned in *Features*, like: missing keyboard definition, missing autoexec edit feature, etc. 

I run this on an old **Raspberry PI 1 Model B**, the last one with **analog video out** with a 512mb SD card; it's just funny to spend a nice [DOScember](https://www.urbandictionary.com/define.php?term=DOScember) and running some old DOS software; for gaming pruposes I use different hardware and different software.

If you have my same setup and you want to connect RPI to an old analog monitor edit `config.txt` in SD root as follow:
```
hdmi_ignore_hotplug=1 # Ignore HDMI Output
sdtv_mode=0 # Set NTSC
```

Where `sdtv_mode` value can be different depending on encoding system used by your TV or Monitor.

| Value | Encoding | 
|-------|----------|
| 0 | NTSC |
| 1 | JAP-NTSC |
| 2 | PAL |
| 3 | BR-PAL |

## Credits
* [**Faux86**](https://github.com/jhhoward/Faux86) has been developed by [**John Howard**](https://github.com/jhhoward/)
* **Faux86** was originally based on [**Fake86**](https://web.archive.org/web/20180817070452/http://fake86.rubbermallet.org/) by **Mike Chambers**; now developed as [**XTulator**](https://github.com/mikechambers84/XTulator). A lot of the code has been shuffled around or rewritten in C++ but the core CPU emulation remains mostly the same.
* [**Circle**](https://github.com/rsta2/circle) to interface with the Raspberry Pi

## License
Released under [**GNU General Public License v2**](https://www.gnu.org/licenses/old-licenses/lgpl-2.0.html) as per [LICENSE](https://github.com/cttynul/f86-dos/blob/master/LICENSE) file stored in this repository.
