---
layout: default
---

## 安装

### i386-pc

```batch
grub-install.exe --no-floppy --target=i386-pc --boot-directory=X:\boot //./PHYSICALDRIVE#
```

### i386-efi

```batch
grub-install.exe --no-nvram --removable --target=i386-efi --boot-directory=X:\boot --efi-directory=Y:
```

### x86_64-efi

```batch
grub-install.exe --no-nvram --removable --target=x86_64-efi --boot-directory=X:\boot --efi-directory=Y:
```

### arm64-efi

```batch
grub-install.exe --no-nvram --removable --target=arm64-efi --boot-directory=X:\boot --efi-directory=Y:
```
