# all: uInitrd
unpack: initrd
initrd.gz: ./uInitrd.org
	dd if=$< of=$@ skip=64 bs=1

initrd: initrd.gz
	gunzip $<
	test -d root || mkdir root
	cd root; cpio -i --make-directories < ../$@

uInitrd:
	( cd root.1; find . | cpio --quiet -o -H newc  > ../initrd )
	gzip -9 initrd; 
	mv initrd.gz initrd 
	mkimage -C none -A arm -O linux -T ramdisk -a 0x0 -e 0x0 -n initrd -d initrd uInitrd
	# mount /dev/mmcblk0p1 /flash
	# cp uInitrd /flash
	# sync
	# umount /flash
	
clean:
	rm -f initrd
	rm -f uInitrd
