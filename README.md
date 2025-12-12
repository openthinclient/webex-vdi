# How to create rootfs
- Install package in openthinclient croot with overlayfs
- also install libjpeg8 from https://archive.debian.org/debian/pool/main/libj/libjpeg8/libjpeg8_8b-1_amd64.deb
- Copy all the neccesary stuff into package-rootfs
- patch libwme.so
  - use execstack from here: https://github.com/skeeto/scratch/blob/master/parsers/execstack.c
  - compile with `gcc execstack.c`
  - `./a.out -c package-rootfs/opt/cisco/TeamsVDI/libwme.so`
- prepare the log folders (the vdi plugin will not work otherwise)
```bash
chmod 777 package-rootfs/var/log/ciscouvdi/
chmod 777 package-rootfs/var/log/CiscoWebexVDI/
touch package-rootfs/var/log/ciscouvdi/.empty
touch package-rootfs/var/log/CiscoWebexVDI/.empty
```
