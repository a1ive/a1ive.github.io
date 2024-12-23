# ISO Loopback Cheatcodes

## Ubuntu-based
iso-scan/filename=${iso_path} boot=casper

## Debian-based
findiso=${iso_path} boot=live

## Fedora-based
### Live
iso-scan/filename=${iso_path} root=live:CDLABEL=${cd_label} rd.live.image
### DVD & Netinstall
iso-scan/filename=${iso_path} inst.stage2=hd:LABEL=${cd_label}

## Arch-based
img_loop=${iso_path} img_dev=/dev/disk/by-uuid/${rootuuid}
iso_loop_path=${iso_path} iso_loop_dev=/dev/disk/by-uuid/${rootuuid}
archisolabel=${cd_label} archisobasedir=arch archisodevice=/dev/loop0 earlymodules=loop modules-load=loop
parabolaisolabel=${cd_label}
hyperisolabel=${cd_label}
kdeisolabel=${cd_label}
chakraisolabel=${cd_label}
