# Aquarius-barebones

### Building kernel
These are the first steps recommended in the DevOS tutorials to get started with kernel writing. To build the kernel follow these steps:
```shell
$ i686-elf-as boot.s -o boot.o
$ i686-elf-gcc -c kernel.c -o kernel.o -std=gnu99 -ffreestanding -O2 -Wall -Wextra
$ i686-elf-gcc -T linker.ld -o myos.bin -ffreestanding -O2 -nostdlib boot.o kernel.o -lgcc
```
### Making bootable CD

To build this we will integrate grub into the file. We will need `grub-mkrescue` and the `xorriso` utility.

```shell
$ mkdir -p /tmp/aquarius/boot/grub
$ cp myos.bin /tmp/aquarius/boot/myos.bin
$ cp boot/grub.cfg /tmp/aquarius/boot/grub/grub.cfg
$ grub-mkrescue -o myos.iso /tmp/aquarius
```
