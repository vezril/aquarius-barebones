Aquarius-barebones

These are the first steps recommended in the DevOS tutorials to get started with kernel writing. To build the kernel follow these steps:
$ i686-elf-as boot.s -o boot.o
$ i686-elf-gcc -c kernel.c -o kernel.o -std=gnu99 -ffreestanding -O2 -Wall -Wextra
$ i686-elf-gcc -T linker.ld -o myos.bin -ffreestanding -O2 -nostdlib boot.o kernel.o -lgcc
