# Cadmium, Linux for ARM chromebooks that don't get attention elsewhere
### It also doesn't suck!

<p align="center">
<img src="/pics/duet_small.png" alt="Lenovo Duet running Linux" data-canonical-src="/pics/duet_small.png"/></p>

## Installation
- ``` ./build-all /dev/sdX ``` On a Linux machine(ChromeOS doesn't count(except in linux chroot)). For Debian rootfs, binfmt and debootstrap are needed to work correctly.
- When ```build-all``` is ran like ```./build-all <file> <size>```, it builds Cadmium to <file> with size of <size>(2G should be fine)
- Enable developer mode
- Plug pendrive into duet via usb-c to usb-a adapter
- Boot from USB
- After running ``` ./install-to-emmc ``` after connecting to internet, Cadmium will be installed on internal emmc memory
- To update kernel on eMMC memory run: ```./install-kernel``` from pendrive

### OR
- Enable developer mode(instructions are in the wiki for duet)
- Write uncompressed release image to pendrive
- Boot from USB
- Run ```./install-to-emmc```

#### *Binary drivers are unsupported in Cadmium and never will be*

## Dependencies on build machine
- Recent Linux distribution
- Binfmt when Debian rootfs is used
- ```debootstrap``` when Debian rootfs is used
- ```qemu-user-static``` when build machine can't run binaries for target machine
- ```vboot_utils u-boot-tools``` (vbutil_kernel, cgpt and mkimage) to pack kernel into format understandable by depthcharge
- ```gcc-aarch64-linux-gnu``` for compiling to ARM
- ```curl``` to download the kernel
- ```bsdtar``` for writing the archive file
- ```f2fs-tools``` for working with the chromebook's eMMC storage
- Build dependencies for kernel compilation

| Hardware support        	| Duet               	| Kevin          	| Asus C100PA and C201PA	|
|-------------------------	|--------------------	|----------------	|-------------------------	|
| Display                 	| Y(needs patches)   	| Y(DP needs FW) 	| Y				|
| Display autorotation    	| Y                  	| N              	| N				|
| Hardware video decoding	| N			| P			| P				|
| Touchscreen             	| Y                  	| Y              	| Y				|
| WiFi                    	| Y(FW)              	| Y(FW)          	| Y(FW)				|
| 3D Acceleration         	| Y                  	| Y              	| Y				|
| Audio                   	| P(speakers broken) 	| Y              	| Y				|
| Bluetooth               	| Y                  	| ?              	| ?				|
| Camera                  	| N                  	| Y              	| Y				|
| USB                     	| Y                  	| Y              	| Y				|
| USB Gadget              	| P                  	| ?              	| ?				|
| Suspending and resuming 	| P                  	| Y              	| P(Dislikes USB booting)	|
| eMMC installation       	| Y                  	| Y              	| Y				|
| KVM Virtualtization		| Y(read wiki)		| Y(read wiki)		| ?				|
