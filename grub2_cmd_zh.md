---
layout: default
---

## 命令列表

### \[ EXPRESSION \]

​    同 “test”

### acpi [OPTIONS] FILE1 [FILE2 ...]

​    加载 ACPI 表

​    现代 BIOS 系统通常实现了 ACPI，并定义各种表来描述符合 ACPI 的操作系统和固件之间的接口。 在某些情况下，默认情况下提供的表仅适用于某些操作系统，并且可能有必要替换其中的某些表。

​    通常，此命令将替换扩展 BIOS 数据区域中的根系统描述指针(RSDP)，以指向新表。 如果使用--no-ebda选项，则仅有 GRUB 获取新表，但 GRUB 的 EFI 仿真可以使用新表。

- \-\-exclude=TABLE1,TABLE2,..., -x 不加载列表
- \-\-load-only=TABLE1,TABLE2,..., -n 加载列表
- \-\-v1, -1 将版本1的表导入操作系统
- \-\-v2, -2 将版本2和3的表导入操作系统
- \-\-oemid=STRING, -o 设置 RSDP, XSDT 和 RSDT 的 OEMID
- \-\-oemtable=STRING, -t 设置 RSDP, XSDT 和 RSDT 的 OEMTABLE ID
- \-\-oemtablerev=n, -r 设置 RSDP, XSDT 和 RSDT 的 OEMTABLE 版本
- \-\-oemtablecreator=STRING, -c Set creator field of RSDP, XSDT and RSDT.
- \-\-oemtablecreatorrev=n, -d Set creator revision of RSDP, XSDT and RSDT.
- \-\-no-ebda, -e 不更新 EBDA。可以防止部分 BIOS 死机，对无法从 GRUB 接收 RSDP 的 OS 无效。

### background_image [OPTIONS] [FILE]

​    为激活的终端设置背景图片

​    默认情况下图像会被拉伸以填满整个屏幕 (--mode=stretch)

​    若不带参数，则删除当前加载的背景图像。

- \-\-mode=stretch/normal, -m 设置背景图模式为拉伸或正常

### **blscfg** FILE

​    导入 BootLoaderSpec (BLS) 配置

### **bls_import** FILE

​    同 "blscfg"

### **btrfs-info** DEVICE

​    显示设备的 btrfs 分区信息

### **btrfs-mount-subvol** DEVICE DIRECTORY SUBVOL

​    设置 btrfs 设备 DIRECTORY 目录为子卷 SUBVOL 的挂载点

### **btrfs-list-subvols** [OPTIONS] DEVICE

​    显示设备 DEVICE 上所有子卷

- \-\-output=VARIABLE, -o 将输出保存为变量
- \-\-path-only, -p 仅显示子卷的路径
- \-\-id-only, -i 仅显示子卷的 id

### **btrfs-get-default-subvol** [OPTIONS] DEVICE

​    显示设备 DEVICE 上的默认子卷

- 参数同 btrfs-list-subvols

### cat [OPTIONS] FILE

​    显示文本文件内容

- \-\-dos 允许 DOS 格式换行符 (CR-LF)
- **\-\-set=VARIABLE, -s 将内容保存到变量**

### chainloader [--force\|--bpb] FILE **[ADDR]**

​    启动另一 bootloader，默认加载地址为 0x7c00

### chainloader [OPTIONS] FILE CMDLINE

​    启动 EFI 可执行文件

​    **警告：使用此命令可能会导致安全方面的问题**

- **\-\-alt, -a 使用 GRUB 2 内置的 EFI 加载器**
- **\-\-text, -t 在启动 EFI 前转换为文本模式**
- **\-\-boot, -b 立即执行启动**

### **checktime** minute hour day month day_of_week

​    检查当前时间是否满足要求，是则返回0，否则返回1。语法与 unix 下的 cron 类似。

| 符号 | 意义                  | 示例     |
| :--: | :-------------------- | -------- |
| \\*  | 任意值 (注意星号转义) | \\*      |
|  ,   | 列举多个值            | 10,20,30 |
|  -   | 范围值                | 5-45     |
|  /   | 步进值                | 10/5     |

### **clear_menu**

​    清空当前菜单

​    **警告：使用本命令前请务必禁用ESC export grub_disable_esc=1**

### **commandline**

​    进入 GRUB 命令行

### **crc32** FILE [VARIABLE]

​    计算文件的 CRC32 校验码

### cpuid [OPTIONS]

​    检测 CPU 特性

​    若不加参数，则默认参数为 -l。若 CPU 支持该特性，则返回 0。

- \-\-long-mode, -l 检测 CPU 是否支持64位长模式
- \-\-pae, -p 检测 CPU 是否支持物理地址扩展 (PAE)

### cryptomount DEVICE | -u UUID | -a | -b

​    挂载加密设备 (支持 LUKS/geli)，某些情况下需要交互输入密码

- \-\-uuid, -u 按 UUID 挂载设备
- \-\-all, -a 挂载所有设备
- \-\-boot, -b 挂载所有带"boot"标记的设备

### date [OPTIONS] [[year-]month-day] [hour:minute[:second]]

​    显示/设置当前时间

- **\-\-set=VARIABLE, -s 将时间保存到变量**

### **decrement** VARIABLE

​    使变量的值减一

### **dd** OPTIONS

​    将文件/字符串/十六进制数写入文件

​    **警告：使用此命令会造成数据损失**

- \-\-if=FILE, -i 指定输入文件
- \-\-str=STRING, -s 指定输入字符串
- \-\-hex=HEX, -h 指定输入十六进制数
- \-\-of=FILE, -o 指定输出文件
- \-\-bs=BYTES, -b 指定块大小
- \-\-count=n, -c 指定块数目
- \-\-skip=n 跳过输入的前n个块
- \-\-seek=n 跳过输出的前n个块

### **dp** FILE/DEVICE

​    输出设备或文件的 UEFI Device Path

### echo [OPTIONS] STRING ...

​    显示字符串

​    若不加 -n 选项，则会自动换行。反斜杠转义支持以下序列：

​    \\\ -- 反斜杠 \a -- 报警(BEL) \c -- 禁止尾随换行 \f -- 换页

​    \n -- 换行 \r -- 回车 \t -- 水平制表符 \v -- 垂直制表符

- -n 不自动换行
- -e 启用反斜杠转义解析

### **efi-export-env** VARIABLE

​    将 GRUB 变量保存到 EFI 环境变量 GRUB_ENV 中

​    **警告：使用此命令会修改 UEFI 环境变量**

### **efi-load-env**

​    从 EFI 环境变量 GRUB_ENV 中读取变量

### **efiload** [OPTIONS] FILE

​    加载 UEFI 驱动

- \-\-nc, -n 仅加载驱动，不进行连接

### export VARIABLE**[=VALUE]** ...

​    将变量设置为全局环境变量

### **expr** [OPTIONS] EXPRESSION

​    计算数学表达式，支持 + - \* \ % 运算符

​    **警告：除以零会导致死机或重启等意外情况**

- \-\-set=VARIABLE, -s 将结果保存到变量

### file OPTIONS FILE

​    检测文件类型

- \-\-is-i386-xen-pae-domu
- \-\-is-x86_64-xen-domu
- \-\-is-x86-xen-dom0
- \-\-is-x86-multiboot
- \-\-is-x86-multiboot2
- \-\-is-arm-linux
- \-\-is-arm64-linux
- \-\-is-ia64-linux
- \-\-is-mips-linux
- \-\-is-mipsel-linux
- \-\-is-sparc64-linux
- \-\-is-powerpc-linux
- \-\-is-x86-linux
- \-\-is-x86-linux32
- \-\-is-x86-kfreebsd
- \-\-is-i386-kfreebsd
- \-\-is-x86_64-kfreebsd
- \-\-is-x86-knetbsd
- \-\-is-i386-knetbsd
- \-\-is-x86_64-knetbsd
- \-\-is-i386-efi
- \-\-is-x86_64-efi
- \-\-is-ia64-efi
- \-\-is-arm64-efi
- \-\-is-arm-efi
- \-\-is-riscv32-efi
- \-\-is-riscv64-efi
- \-\-is-hibernated-hiberfil
- \-\-is-x86_64-xnu
- \-\-is-i386-xnu
- \-\-is-xnu-hibr
- \-\-is-x86-bios-bootsector

### **getargs** OPTIONS STRING VARIABLE

​    从 GRUB 2 EFI 文件接收到的命令行获取参数

- \-\-key, -k 获取是否设定此参数
- \-\-value, -v 获取参数的值

### **getenv** [OPTIONS] EFI_ENV VARIABLE

​    获取 UEFI 环境变量

- \-\-guid=GUID, -g 设置要查询变量的 GUID，默认为全局变量
- \-\-type=string/uint8/hex, -t 指定变量类型为字符串/8比特无符号整数/十六进制数据，默认为十六进制数据

### **getkey** [-n] [VARIABLE]

​    等待按键并输出键盘扫描码

### gettext STRING

​    将字符串翻译成当前语言

​    当前的语言代码存储在 GRUB 环境中的"lang"变量中。 MO格式的翻译文件是从“ locale_dir"中读取的，通常是/boot/grub/locale。

### **gptprio.next** OPTIONS [DEVICE]

​    选择 GPT 磁盘要启动的下一分区

- \-\-set-device=VARIABLE, -d 将分区名保存到变量
- \-\-set-uuid=VARIABLE, -u 将分区 UUID 保存到变量

### **gptrepair** DEVICE

​    校验并修复设备的GPT分区表

​    **警告：使用此命令有可能会造成数据损失**

### hashsum -h HASH [OPTIONS] [-c FILE [-p PREFIX]] [FILE1 [FILE2 ...]]

​    计算或校验哈希值，若哈希校验成功，则返回0。

- \-\-hash=HASH, -h 指定哈希值类型，支持 'adler32’, ‘crc64’, ‘crc32’, ‘crc32rfc1510’, ‘crc24rfc2440’, ‘md4’, ‘md5’, ‘ripemd160’, ‘sha1’, ‘sha224’, ‘sha256’, ‘sha512’, ‘sha384’, ‘tiger192’, ‘tiger’, ‘tiger2’, ‘whirlpool’
- \-\-check=FILE, -c 指定哈希列表文件(在 UNIX 下使用 md5sum 生成)
- \-\-prefix=PREFIX, -p 指定文件目录
- \-\-keep-going, -k 第一次出错后不停止检验，不加此选项则停止检验
- \-\-uncompress, -u 在校验前解压文件

### hdparm [OPTIONS] DISK

​    获取/设置 ATA 磁盘参数

- \-\-apm=n, -B 设置高级电源管理 (APM)，1=低，...，254=高，255=关
- \-\-power, -C 显示电源模式
- \-\-security-freeze, -F 冻结ATA安全设置直到重置
- \-\-health, -H 显示 SMART 健康状态
- \-\-aam=n, -M 设置自动噪声管理 (AAM)，0=关，128=安静，...，254=快速
- \-\-standby-timeout=n, -S 设置待机超时，0=关，1=5s，2=10s，...，240=20m，241=30m，...
- \-\-standby, -y 设为待机模式
- \-\-sleep, -Y 设为睡眠模式
- \-\-identify, -i 显示设备标识和设置
- \-\-dumpid, -I 显示 ATA IDENTIFY 扇区的原始内容
- \-\-smart=n 禁用/启用 SMART (0/1)
- \-\-quiet, -q 不显示信息

### help [PATTERN ...]

​    显示内置命令的帮助信息。如果未加参数，则显示所有可用命令。

### hexdump [OPTIONS] FILE/DEVICE **[VARIABLE]**

​    显示文件或设备的十六进制数据。(mem)为内存设备。

- \-\-skip=n, -s 跳过起始n字节
- \-\-length=n, -n 设置读取字节数
- **\-\-quiet, -q 不显示输出**

### **hiddenentry** "TITLE" --hotkey=KEY { COMMANDS }

​    添加隐藏菜单，仅对 gfxmenu 有效。

### **imgwrite** FILE DEVICE

​    将文件写入磁盘

​    **警告：使用此命令会造成数据损失**

### inb [OPTIONS] PORT

​    从端口读取8比特数值

- -v=VARIABLE 将读到的数值写入变量

### **increment** VARIABLE

​    使变量的值加一

### **ini_get** [OPTIONS] FILE [SECTION:]KEY

​    从 ini 文件获取数据

- \-\-set=VARIABLE, -s 将数据保存到变量

### **initrdefi** FILE

​    加载 Linux 初始内存盘，在 linuxefi 之后使用

### inl [OPTIONS] PORT

​    从端口读取32比特数值，参数同 "inb"

### inw [OPTIONS] PORT

​    从端口读取16比特数值，参数同 "inb"

### keystatus [OPTIONS]

​    若 Shift/Ctrl/Alt 键按下，则返回 0

​    只有部分平台支持检测修饰键状态，若不加任何参数，则此命令用于检测是否支持修饰健状态。

- \-\-shift, -s 检测 Shift 键
- \-\-ctrl, -c 检测 Ctrl 键
- \-\-alt, -a 检测 Alt 键

### kfreebsd [OPTIONS] FILE [CMDLINE]

​    加载 FreeBSD 内核

### kfreebsd_loadenv FILE

   加载 FreeBSD 环境变量

### kfreebsd_module FILE [CMDLINE]

​    加载 FreeBSD 模块

### kfreebsd_module_elf FILE [CMDLINE]

​    加载 FreeBSD 模块 (ELF)

### knetbsd [OPTIONS] FILE [CMDLINE]

​    加载 NetBSD 内核

### knetbsd_module FILE [CMDLINE]

​    加载 NetBSD 模块

### knetbsd_module_elf FILE [CMDLINE]

​    加载 NetBSD 模块 (ELF)

### kopenbsd [OPTIONS] FILE [CMDLINE]

​    加载 OpenBSD 内核

### kopenbsd_ramdisk FILE

​    加载 OpenBSD 内存盘

### **linuxefi** FILE [CMDLINE]

​    加载 Linux 内核

### list_env [OPTIONS]

​    列出环境块文件中的所有变量

- \-\-file=FILE, -f 指定文件名，默认文件名为 ${prefix}/grubenv
- \-\-skip-sig, -s 跳过环境文件的签名检查

### load_env [OPTIONS] [VARIABLE ...]

  从环境块文件加载变量，参数同 "list_env"

### loopback [OPTIONS] DEVICE FILE

​    将文件挂载为虚拟盘

- \-\-delete, -d 删除指定的虚拟盘
- **\-\-mem, -m 将文件复制到内存并挂载，允许写入操作**

### **lsefienv**

​    列出所有 EFI 环境变量

### **lua** [FILE]

​    执行 Lua 脚本

### map [OPTIONS] FILE

​    创建 UEFI 虚拟盘并启动

- \-\-mem, -m 加载到内存
- \-\-pause, -p 启动前暂停以查看信息
- \-\-type=CD/HD/FD, -t 指定磁盘类型为光盘/硬盘/软盘
- \-\-disk, -d 仿真整个磁盘
- \-\-rw, -w 允许写入虚拟盘，仅对内存盘有效
- \-\-nb, -n 不启动此虚拟盘

### **moksbset**

​    暂时禁用 shim 安全验证，需要重新启动

​    **警告：使用此命令会修改 UEFI 环境变量**

​    **警告：使用此命令可能会导致安全方面的问题**

### **ntboot** [OPTIONS] FILE

​    启动 NT6+ VHD/VHDX/WIM

- \-\-gui, -g 启用图形启动信息
- \-\-pause, -p 启动前暂停
- \-\-vhd, -v 指定文件类型为 VHD/VHDX
- \-\-wim, -w 指定文件类型为 WIM
- \-\-efi=FILE, -e 指定 bootmgfw.efi 路径，默认为 /efi/microsoft/boot/bootmgfw.efi
- \-\-sdi=FILE, -s 指定 boot.sdi 路径，默认为 /boot/boot.sdi

### outb PORT VALUE [MASK]

​    向端口写入8比特数值

### outl PORT VALUE [MASK]

​    向端口写入32比特数值

### outw PORT VALUE [MASK]

​    向端口写入16比特数值

### **partnew** OPTIONS DISK PARTNUM

​    为 msdos 分区表的磁盘创建主分区

​    **警告：使用此命令有可能会造成数据损失**

- \-\-active, -a 激活该分区
- \-\-file=FILE, -f 将文件作为分区内容使用
- \-\-type=HEX, -t 指定分区类型，0x00为自动，0x10为自动隐藏
- \-\-start=n, -s 指定开始地址(单位为扇区)
- \-\-length=n, -l 指定长度(单位为扇区)

### **peinfo** FILE

​    查看 PE (Portable Executable) 文件头

### **pop_env** VARIABLE ...

​    将子菜单中的变量传递给上一级菜单

### probe OPTIONS DEVICE

​    检测设备信息

- \-\-set=VARIABLE, -s 将返回值设为变量
- \-\-driver, -d 检测驱动
- \-\-partmap, -p 检测分区表类型
- \-\-fs, -f 检测文件系统类型
- \-\-fs-uuid, -u 检测文件系统 UUID
- \-\-label, -l 检测文件系统卷标
- \-\-partuuid, -g 检测分区 UUID (GPT分区表)
- **\-\-bootable, -b 检测是否激活 (msdos分区表)**
- **\-\-quiet, -q 不显示报错**

### **rand** [OPTIONS] VARIABLE

​    生成伪随机数

- \-\-from=n, -f 设置随机数下界
- \-\-to=n, -t 设置随机数上界

### **read_file** FILE VARIABLE ...

​    读取文件，将文件的内容逐行设置为变量

### **sbpolicy** [OPTIONS]

​    安装绕过安全启动的安全策略

​    **警告：使用此命令可能会导致安全方面的问题**

- \-\-install, -i 安装安全策略
- \-\-uninstall, -u 卸载安全策略
- \-\-status, -s 显示安全策略状态

### search OPTIONS STRING

​    搜索磁盘

- \-\-file, -f 按文件搜索
- \-\-label, -l 按文件系统卷标搜索
- \-\-fs-uuid, -u 按文件系统 UUID 搜索
- \-\-part-label, -L 按分区卷标搜索
- **\-\-part-uuid, g 按分区 UUID 搜索 (GPT)**
- **\-\-disk-uuid, U 按磁盘 UUID 搜索 (GPT)**
- \-\-set=VARIABLE, -s 将第一个找到的设备保存到变量
- \-\-no-floppy, -n 不检测软盘
- **\-\-quiet, -q 如果没有匹配，不显示错误**
- \-\-hint=HINT, -h 指定先从某设备开始搜索，如果以逗号结束，则也会搜索子分区
- \-\-hint-ieee1275=HINT 如果运行于 IEEE1275 环境下，指定先从某设备开始搜索
- \-\-hint-bios=HINT 如果运行于 BIOS 环境下，指定先从某设备开始搜索
- \-\-hint-baremetal=HINT 如果运行于 baremetal 环境下，指定先从某设备开始搜索
- \-\-hint-efi=HINT 如果运行于 EFI 环境下，指定先从某设备开始搜索
- \-\-hint-arc=HINT 如果运行于 ARC 环境下，指定先从某设备开始搜索

### **setenv** [OPTIONS] EFI_ENV VALUE

​    写入 UEFI 环境变量

​    **警告：使用此命令会修改 UEFI 环境变量**

​    **警告：使用此命令可能会导致安全方面的问题**

- \-\-guid=GUID, -g 设置要写入变量的 GUID，默认为全局变量
- \-\-type=string/uint8/hex, -t 指定变量类型为字符串/8比特无符号整数/十六进制数据，默认为十六进制数据

### **shell** [OPTIONS] CMDLINE

​    启动 UEFI Shell

- \-\-nostartup 不执行默认启动脚本
- \-\-noconsoleout 不显示终端输出
- \-\-noconsolein 不接收用户输入
- \-\-delay=n 设置执行启动脚本前等待时间
- \-\-nomap 不显示设备映射列表
- \-\-noversion 不显示版本信息
- \-\-startup 执行默认启动脚本
- \-\-nointerrupt 禁止中断执行过程
- \-\-exit 命令执行完成后自动退出
- \-\-device=DEVICE 指定默认 Device Path

### **strconv** [OPTIONS] STRING

​    字符串 UTF-8/GBK 编码转换

- \-\-gbk, -g UTF-8 -> GBK
- \-\-utf8, -u GBK -> UTF-8 (默认)
- \-\-set=VARIABLE, -s 将返回值设为变量

### **submenu_exit**

​    从当前子菜单退出

### **tetris**

​    俄罗斯方块游戏。请先执行 terminal_output console

### **uuid4** VARIABLE

​    生成 UUID 字符串

### **vboot** harddisk=FILE floppy=FILE cdrom=FILE boot=harddisk/floppy/cdrom

​    进行 vboot 启动，指定硬盘镜像/软盘镜像/光盘镜像与默认启动设备。

​    必须先执行 vbootinsmod 加载 vbootcore.mod。

​    硬盘上需要含有vboot文件。

​    vboot的默认路径为/vboot/vboot，修改变量 vbootloader 以指定路径。

### **vbootinsmod** FILE

​    加载 vboot 核心文件 vbootcore.mod

### **vfat** OPTIONS

​    UEFI 虚拟 FAT 磁盘操作

- \-\-create, -c 创建虚拟 FAT 磁盘

- \-\-add=NAME FILE, -a 指定将文件 FILE 加入虚拟盘，虚拟盘内文件名为 NAME

- \-\-mem, -m 指定文件载入内存，允许写入文件

- \-\-install, -i 使虚拟盘在 UEFI 中可见

- \-\-boot, -b 启动虚拟盘

- \-\-ls, -l 列出虚拟盘中所有文件

- \-\-patch=FILE STRING, -p 指定要修改的文件名，文件必须在内存中

- \-\-offset=n, -o 指定修改的偏移量

- \-\-search=STRING, -s 搜索字符串

- \-\-count=n, -c 指定搜索次数

  搜索及替换的字符串支持以下格式

  | 格式                    | 类型       | 示例输入 | 示例输出        |
  | ----------------------- | ---------- | -------- | --------------- |
  | sSTRING 以's'开头       | 普通字符串 | sHello   | Hello           |
  | wSTRING 以'w'开头       | 宽字符串   | wWin32   | W\0i\0n\03\02\0 |
  | STRING 开头不是's'或'w' | 十六进制   | 74657374 | test            |

### **vhd** [OPTIONS] DEVICE FILE

​    将 vhd 文件挂载为虚拟盘

- \-\-delete, -d 删除虚拟盘
- \-\-partitions -p 模拟带分区的硬盘

### **wimboot** [OPTIONS] @:NAME:FILE

​    启动 WIM 文件

- \-\-gui, -g 启用图形启动信息
- \-\-rawbcd, -b 禁用 BCD 自动修改 (.exe 改为 .efi)
- \-\-rawwim, -w 禁用 WIM 自动修改
- \-\-index=n, -i 指定要启动的WIM卷号
- \-\-pause, -p 启动前暂停
- \-\-inject=WIN32_PATH, -j 指定射入文件夹，默认为 \Windows\Syatem32

### **write_bytes** ADDR VALUE ...

​    将一系列8比特数值写到地址 ADDR

​    **警告：使用此命令可能会导致安全方面的问题**

