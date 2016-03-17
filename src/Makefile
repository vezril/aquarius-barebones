# Makefile to compile the barebones aquarius project and to provide a simple practice on writing these
CFLAGS=-ffreestanding -O2
CC=i686-elf-gcc
AS=i686-elf-as
all: kernel iso

kernel:
	$(AS) boot.s -o boot.o
	$(CC) $(CFLAGS) -c kernel.c -o kernel.o -std=gnu99 -Wall -Wextra
	$(CC) $(CFLAGS) -T linker.ld -o myos.bin -nostdlib boot.o kernel.o -lgcc

iso:
	mkdir -p /tmp/aquarius/boot/grub
	cp myos.bin /tmp/aquarius/boot/myos.bin
	cp boot/grub.cfg /tmp/aquarius/boot/grub/grub.cfg
	grub-mkrescue -o myos.iso /tmp/aquarius
	rm -rf /tmp/aquarius

clean:
	rm *.o *.iso *.bin
