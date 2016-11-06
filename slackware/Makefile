# prepare slackware installer partition in 3 partition method.
unpack: root

root:
	( test -d root || mkdir root )
	# mountpoint root || mount /dev/mmcblk0p2 root
	# http://www.arm.slackware.com/slackwarearm/slackwarearm-14.2/isolinux/initrd-armv7.img
	(cd root ; gzip -dc ../initrd-armv7.img | cpio -i --make-directories )
	(cd root ; rm -rf lib/modules/4.4.14-armv7 lib/firmware )
	(cd /ubuntu-16.04.1.lts/lib/modules ; tar cfz - 3.8.13.30 ) | (cd root/lib/modules; tar xfz - )
	(cd /ubuntu-16.04.1.lts/lib; tar cfz - firmware ) | (cd root/lib; tar xfz - )

clean:
	rm -f root
