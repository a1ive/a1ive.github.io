# ISO Loopback Cheatcodes

## Variables
- iso_path  
  the path to the ISO file **without** the device prefix.  
  e.g. `/path/to/iso.iso`
- rootuuid  
  the filesystem UUID of the partition where the ISO file is located.  
- cd_label  
  the filesystem label of the loopback device (ISO).  
- loopuuid  
  the filesystem UUID of the loopback device (ISO).  

You can use the following command to get these values:  
```bash
  set iso_path=/path/to/iso.iso
  export iso_path
  search --set=root --file $iso_path
  loopback loop $iso_path
  set root=loop
  probe --set=rootuuid --fs-uuid ($root)
  export rootuuid
  probe --set=cd_label --label (loop)
  export cd_label
  probe --set=loopuuid --fs-uuid (loop)
  export loopuuid
```

## Ubuntu-based
```
iso-scan/filename=${iso_path} boot=casper
```

## Debian-based
```
findiso=${iso_path} boot=live
```

## Fedora-based
### LiveCD / openSUSE
```
iso-scan/filename=${iso_path} root=live:CDLABEL=${cd_label} rd.live.image
```

### DVD & Netinstall
```
iso-scan/filename=${iso_path} inst.stage2=hd:LABEL=${cd_label}
```

### Minimal Install
```
iso-scan/filename=${iso_path} inst.stage2=hd:UUID=${loopuuid}
```

## Arch-based
### Live ISO
```
img_loop=${iso_path} img_dev=/dev/disk/by-uuid/${rootuuid}
```

### Archboot
```
iso_loop_path=${iso_path} iso_loop_dev=/dev/disk/by-uuid/${rootuuid}
```

### Extra parameters may be needed
```
archisolabel=${cd_label} archisobasedir=arch archisodevice=/dev/loop0 earlymodules=loop modules-load=loop
```

### Other Arch-based distros
- Parabola
- Hyperbola
- KaOS
- Chakra
```
parabolaisolabel=${cd_label}
hyperisolabel=${cd_label}
kdeisolabel=${cd_label}
chakraisolabel=${cd_label}
```

## Gentoo-based
```
isoboot={iso_path}
```

## Deepin
```
fromiso=${iso_path} findiso=${iso_path}
```

## Siduction
```
fromiso=${iso_path}
```

## System Rescue CD
### Gentoo-based
```
isoloop=${iso_path}
```

### Arch-based
```
img_loop=${iso_path} img_dev=/dev/disk/by-uuid/${rootuuid} archisolabel=${cd_label}
```

## IPFire
```
bootfromiso=${iso_path}
```

## PCLinuxOS
```
root=UUID=${rootuuid} isoboot=${iso_path}
```

## Calculate Linux
```
isoboot=${iso_path} root=live:LABEL=${looplabel} iso-scan/filename=${iso_path}
```

## Android-x86
```
iso-scan/filename=${iso_path}
```

## Slax / Porteus
```
fromiso=${iso_path}
```

## WifiSlax
### WifiSlax64
```
livemedia=/dev/disk/by-uuid/${rootuuid}:${iso_path}"
```

### Older versions
```
fromiso=${iso_path}
```

### Wifiway
```
from=${iso_path}
```

## Veket
```
find_iso=${iso_path}
```

## Parted Magic
```
iso_filename=${iso_path}
```

## Plop Linux
```
iso_filename=${iso_path}
```

## Slackware
```
livemedia=scandev:${iso_path}
```

## antiX / MX Linux
```
fromiso=${iso_path} from=hd,usb
```

## ALT Linux
```
automatic=method:disk,uuid:${rootuuid},directory:${iso_path}
```

## Austrumi
```
sr=${iso_path}
```

## CDlinux
```
CDL_DEV=UUID=${rootuuid} CDL_IMG=${iso_path} CDL_DIR=/
```

## TinyCore
```
iso=UUID=${rootuuid}${iso_path}
```

## Knoppix
```
bootfrom=/dev/*${iso_path}
```
