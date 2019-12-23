---
layout: default
---

# GRUB 2 中文手册

## 命令

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

### **gptprio.next** OPTIONS [DEVICE]

​    选择 GPT 磁盘要启动的下一分区

- \-\-set-device=VARIABLE, -d 将分区名保存到变量
- \-\-set-uuid=VARIABLE, -u 将分区 UUID 保存到变量

### **gptrepair** DEVICE

​    校验并修复设备的GPT分区表

​    **警告：使用此命令有可能会造成数据损失**

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

### **increment** VARIABLE

​    使变量的值加一

### **ini_get** [OPTIONS] FILE [SECTION:]KEY

​    从 ini 文件获取数据

- \-\-set=VARIABLE, -s 将数据保存到变量

### **initrdefi** FILE

​    加载 Linux 初始内存盘，在 linuxefi 之后使用

### **linuxefi** FILE CMDLINE

​    加载 Linux 内核

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

## 变量

| 变量名称          | 默认值 | 含义                                |
| ----------------- | ------ | ----------------------------------- |
| grub_prompt       | grub>  | GRUB 命令提示符                     |
| grub_disable_esc  | 0      | 0为允许使用 ESC 热键返回上一级菜单  |
| grub_cmdline      |        | 从上一级 EFI 启动器接收到的命令行   |
| grub_frame_speed  |        | 动画主题帧速，单位为毫秒/帧         |
| grub_sound_speed  |        | 蜂鸣器声音播放速度，单位为毫秒/音符 |
| grub_sound_start  |        | 自定义循环播放音乐                  |
| grub_sound_select |        | 自定义上下键选择菜单音效            |

## 动态主题

### 启用动态主题

```bash
export grub_frame_speed=110
```

其中，110为帧速，单位是毫秒每帧。

在 theme.txt 中使用动画容器

```scss
+ animation {
    dir_name = "IMAGE_DIR"
    image_format = png/jpg/jpeg/tga
    frame_number = n
    left = p%
    width = p%
    top = p%
    height = p%
    size_ratio = n
    start_x = n
    start_y = n
    move_speed = n
    move_direction = up/down/left/right
    play_once = pause/disappear
    hit_wall = pause/stop/disappear
    bind_menu = fixed_position/follow_single/foll_variety/full_screen
    bind_direction = left/right
}
```

### 属性说明

dirname = "IMAGE_DIR"

​    动画序列图片所在文件夹，指 theme.txt 所在目录下的文件夹

image_format = png/jpg/jpeg/tga

​    指定动画图片的扩展名，支持 png, jpg, jpeg, tga

frame_number = n

​    动画序列图片总数

​    图片文件命名必须是数字加扩展名，数字从 1 开始，例如 1.jpg, 2.jpg, 3.jpg ...

left/top/width/height = x/p%/p%+x

​    容器在屏幕中的左边距/上边距/宽度/高度

​    支持格式：百分比(p%), 像素(x), 百分比+像素(p%+x)

size_ratio = n

​    动画大小相对于容器的比例

start_x/start_y = n

​    动画在容器中x/y坐标的偏移值

​    若动画跟随主菜单选择条目的位置而移动，则 start_y 无效。

move_direction = up/down/left/right

​    设置动画初始的移动方向，只在随机移动的动画中有效

move_speed = n

​    设置动画移动速度

​    值为 0，则在原地播放动画。值不能为负数。

play_once = pause/disappear

​    设置动画播放一次后暂停显示最后一帧或消失

​    若不设置此项，则为循环播放。

hit_wall = pause/stop/disappear

​    设置当动画撞到容器壁后的行为

​    pause -- 暂停播放动画

​    stop -- 停止移动，继续播放动画

​    disappear -- 消失

bind_menu = fixed_position/follow_single/foll_variety/full_screen

​    设置动画作为随菜单选项变化的 logo 使用

​    若参数不是 follow_single，则动画序列应该放在 dir_name 参数目录的各子目录中，子目录名与 menuentry --class 的参数相同。

​    fixed_position -- 在固定位置随菜单项播放动画

​    follow_single -- 跟随菜单项，在不同位置显示同一组动画

​    follow_variety -- 跟随菜单项，在不同位置播放不同动画

​    full_screen -- 全屏显示随菜单项变化的动画

bind_direction = left/right

​    在启用跟随菜单项的动画后，设置动画的位置在主菜单左边框的左边或右边

### 菜单音效

设置变量 grub_sound_speed 以启用音效。单位是毫秒每音符

```bash
export grub_frame_speed=110
```

设置循环播放音效

```bash
export grub_sound_start="freq1 freq2 freq3 ..."
```

设置上下键选择菜单音效

```bash
export grub_sound_select="freq1 freq2 freq3 ..."
```

其中 freq1, freq2, freq3 ... 是频率，单位为赫兹

默认音效

```bash
grub_sound_start="220 277 330 440 185 220 277 370 294 370 440 587 330 415 494 659"
grub_sound_select="880 0 880 0 880 698 1046"
```
