---
layout: default
---

## Lua

### 加载 Lua 模块

​    `insmod lua`

### 进入 Lua 交互编程模式

​    在控制台中输入 `lua`

### 执行 Lua 脚本

​    `lua /path/to/script.lua`

### grub 函数库

- grub.run (string)

  执行 GRUB 命令，若执行成功，则返回零，否则返回非零值。

- grub.script (string)

  执行一行 GRUB 脚本，若脚本执行成功则返回零。

- grub.getenv (string)

  获取 GRUB 环境变量的值，若环境变量存在，则返回字符串，否则，返回 `nil`。

- grub.setenv
- grub.exportenv
- grub.enum_device
- grub.enum_file
- grub.enum_pci
- grub.file_open
- grub.file_close
- grub.file_seek
- grub.file_read
- grub.file_write
- grub.file_getline
- grub.file_getsize
- grub.file_getpos
- grub.file_eof
- grub.file_exist
- grub.file_crc32
- grub.disk_open
- grub.disk_close
- grub.disk_read
- grub.disk_write
- grub.hexdump
- grub.add_menu
- grub.add_icon_menu
- grub.add_hidden_menu
- grub.clear_menu
- grub.read_byte
- grub.read_word
- grub.read_dword
- grub.write_byte
- grub.write_word
- grub.write_dword
- grub.cls
- grub.setcolorstate
- grub.refresh
- grub.read
- grub.gettext
- grub.get_time_ms
- grub.random
- grub.disk_getsize

### input 函数库

- input.getkey
- input.getkey_noblock
- input.read

### video 函数库

- video.swap_buffers
- video.fill_rect
- video.draw_string
- video.info

### gbk 函数库

- gbk.len
- gbk.byte
- gbk.char
- gbk.fromutf8
- gbk.toutf8